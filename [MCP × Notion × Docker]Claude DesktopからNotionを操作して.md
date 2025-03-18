---
tags:
  - AI
---
#mcp #Notion #Docker 
作成日: 2025/03/06
URL: https://qiita.com/mkthrkw/items/5cb77065806a7eb99082

## はじめに

巷で話題の **Model Context Protocol (MCP)** 。

なんとClaude for Desktop から **Notion** のページ操作ができるとのことで、実際に試してみました！

他にも **ローカルファイル操作** や **データベース連携** など、今後の拡張性にワクワクする仕組みです。

nodeやpythonなどはローカルには入れずにやりたいので、

今回は **Docker** でNotionサーバーを立ち上げ、Claude for Desktopと連携をやってみます。

## 参考

MCPはAI（人工知能）とさまざまなデータやツールをつなぐための新しい仕組みのことで2024年11月26日にAnthropicからリリースされています。

詳しい説明をされている方がたくさんいらっしゃり、いくつも参考にさせていただきました。

docker構築は下記を参考にさせていただきました（ありがとうございます！！！！）

今回の大部分は下記の方の記事を参考にさせていただいています。

mcp serversに載ってなかったのですが、notion serverをなんと実装してPR出している方の

記事を参考にさせていただきdockerを使ってやってみました（凄すぎます・・・）

## やること要約

1. Notionのインテグレーションを作成して、Apiトークン取得
2. 操作するNotionのページIDを取得
3. NotionServerのファイルをクローン（上記の方のリポジトリからになります）
4. Dockerfile関連を作成
5. Claude for Desktopをインストール（無料版でも使えます）
6. Claudeの設定ファイルを編集して、再起動

## Notion準備

Notionのアカウントある前提です（無料版でも使えます）

まず、Notionでデータを操作するためにインテグレーションを作成します。

① [[]] へアクセスします。

② 「**新しいインテグレーション** 」ボタンをクリックします。

③ 必要な情報を入力して作成します。

- **名前** ：任意の名前（例：Claude-MCP-Integration）

- **関連ワークスペース** ：操作したいワークスペース

- **種類** ：デフォルトのInternalでOKです

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F3680973%2Fa61be55a-6f16-e65d-65a8-8ad15baa4b66.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=343508f8aed439ff6781d83682fa48aa)

④ インテグレーションが作成されると、「**内部インテグレーションシークレット** 」が発行されるのでメモしておきます。

（後で環境変数として設定します）

⑤ 操作をしたいNotionページの親ページを作成したインテグレーションに接続する

右上メニュー ＞ 接続先 ＞ 自身で作った接続先

そのページの中に作ったものは同様の接続先として設定できます。

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F3680973%2F396dab0a-31f3-1e37-4fca-725ee732db81.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=90a500438058d1bc879a941821186185)

⑥ 親ページのIDをメモしておく

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F3680973%2F9cf1a8a1-8c6d-297f-b474-e406e6dc2cd9.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=c0acda5cdbf3570a362f80c8c01c9a16)

## Dockerコンテナ作成

### まずはgitからクローン

任意のディレクトリに下記のリポジトリからクローン

```
git clone https://github.com/suekou/mcp-notion-server.git

```

### Docker関連ファイル作成

クローンすると`mcp-notion-server`というディレクトリが作成されるのでその中に

`Dockerfile` , `docker-compose.yml` , `.env`を配置。

```
.
├── Dockerfile  // 作成
├── LICENSE
├── [[]]
├── docker-compose.yml  // 作成
└── notion
    ├── package-lock.json
    ├── package.json
    ├── src
    │   └── index.ts
    └── tsconfig.json

```

Dockerfile

```
# ベースイメージ
FROM node:20-slim

# 作業ディレクトリ
WORKDIR /notion

# 必要なファイルを全てコピー
COPY ./notion /notion

# 依存関係のインストール
RUN npm install

# TypeScriptをビルド
RUN npm run build

# コンテナ起動時のコマンド
CMD ["npm", "run", "start"]

```

docker-compose.yml

```
services:
  mcp-notion-server:
    container_name: mcp-notion-server
    build: .
    environment:
      - NOTION_API_TOKEN=${NOTION_API_TOKEN}
    stdin_open: true  # stdinを開いたままにする
    tty: true        # 疑似TTYを割り当てる

```

.env

```
NOTION_API_TOKEN=<ここに先ほど作成したシークレットキーを記載>

```

### package.jsonへ１行追加

Dockerfile最後に記載した`npm run start`の動作を追加

notion/package.json

```
],
  "scripts": {
    "build": "tsc && node -e \"require('fs').chmodSync('build/index.js', '755')\"",
    "prepare": "npm run build",
    "watch": "tsc --watch",
    "inspector": "npx @modelcontextprotocol/inspector build/index.js",
    "start": "node build/index.js"  ←ここを追加
  },
  "dependencies": {
```

### docker コンテナ起動

```
docker compose up -d

```

無事起動できたら準備OKです！

## Claude for Desktopを設定

### Claude for Desktopインストール

無料版でも使用できます。

### アプリを起動して設定ファイルを編集

Claudeの設定ファイルに先ほど作成したNotionサーバーの情報を追加します。

### `claude/config.json`を開きます。

上部メニューClaude > Settings... > Developer > Edit Config

### Notionサーバーのエンドポイントを設定します。

```
{
  "mcpServers": {
    "notion": {
      "command": "docker",
      "args": [
        "compose",
        "-f",
        "/Users/<username>/<somedir>/mcp-notion-server/docker-compose.yml",
        "exec",
        "-i",
        "mcp-notion-server",
        "npm",
        "run",
        "start"
      ]
    },
  }}
```

### 設定を保存して、Claude for Desktopを再起動します。

バツ閉じだと上手く再起動しないこともあるようなので、

上部メニュー > Claude > Quit でしっかり終了してから再起動。

TOPページのチャットスペースの右下に金槌マークが出てきたら成功となります！

## NotionのページIDを渡して動作テスト

Notionサーバー経由で動作確認を行います。

Claudeに以下のようなプロンプトを送信します：

```
NotionのページID "xxxxxxxxxxxx" の内容を取得して。

```

```
〇〇の内容をまとめて、NotionのページID "xxxxxxxxxxxx" の中に新規にページを作成して。

```

正しくサーバーが動作していれば、何回か許可を求められたあと、

指定したページの情報が取得され、Claudeが返答してくれます。

## まとめ

- これで **Claude for Desktop** と **Notion** の連携ができました👏👏👏
- 調べた結果やリンク一覧などを「Notionにまとめといて」とClaudeに丸投げ出来るので、楽になりますね！
- MCPを活用することで、この他にもさまざまなデータやツールとAIを繋げることが可能になりますので、どんどん試していこうと思います。