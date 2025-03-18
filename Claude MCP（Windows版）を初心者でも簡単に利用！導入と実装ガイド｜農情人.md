---
tags:
  - AI
---
# Claude MCP（Windows版）を初心者でも簡単に利用！導入と実装ガイド｜農情人


作成日: 2025/03/06
URL: https://note.com/noujoujin/n/na3d106e39d6a

![](https://assets.st-note.com/production/uploads/images/164226461/rectangle_large_type_2_a12a5405af7ca1dfd7e654cc6b444806.jpeg?width=1200)

Claude MCPを使ってみたいけど、初めての環境構築に苦戦する人も多いのではないでしょうか？

この記事では、実際に私が導入までに4～5時間かかった中で得た「つまづきポイント」を初心者にも分かりやすく整理してご紹介します。

このガイドを読めば、Claude MCPを利用できるようになるはずです！

## 1. Claude MCPとは

Claude MCP（Model Context Protocol）は、Claudeデスクトップアプリにおける外部サービスやシステムとの連携を可能にする拡張プロトコルです。これを活用すれば、Brave Searchやファイルシステムの統合など、強力な機能を手軽に追加できます。

## 2. つまづきポイントと解決方法

### 2-1 `claude_desktop_config.json` の作成が必要

多くの人が最初に勘違いしやすいのが、**設定ファイルが自動生成されるわけではない**という点です。

- **間違い**：デスクトップ版をインストールすれば、`claude_desktop_config.json` が既に存在すると思っていた。
- **正解**：**自分で新規作成する必要があります**。

**手順**：

1. ファイル名：`claude_desktop_config.json`
2. 保存場所：`%APPDATA%\Claude`（Windowsの場合）
3. ファイルを新規作成し、設定内容を記述します。

### 2-2 Node.jsのバージョン選定

Node.jsのバージョンが最新すぎると、Claude MCPが正しく動作しないリスクがあります。

- **推奨バージョン**：`20.10.0`
- **参考記事**：[Node.jsバージョンの推奨について](https://zenn.dev/channnnsm/articles/6fc50a86a1e03e)

**解決方法**：

1. **nvm（Node Version Manager）**を使用して、推奨バージョンをインストール。

```
bash
nvm install 20.10.0
nvm use 20.10.0
```

2.バージョン確認：

```
bash
node -v
```

### 2-3 JSONファイル内のパス指定

JSONの記述でつまづきやすいポイントは、**Windowsのパス指定方法**です。

- **間違い**：`\` を1つだけ記述。
- **正解**：`\` を2つ（`\\`）記述。

**例**:

```
"args": [
    "C:\\Users\\ユーザー名\\AppData\\Roaming\\npm\\node_modules\\@modelcontextprotocol\\server-filesystem\\dist\\index.js"
]
```

### 2-4 ファイルパスの指定方法

設定ファイルで指定するファイルパスを手動で入力するのはミスの原因になります。**間違いのない方法**として、次の手順をお勧めします。

**解決方法**：

1. 必要なファイルを右クリック。
2. 「**ファイルパスをコピー**」を選択。
3. コピーした内容をJSONに貼り付ける。
- Brave Search用パス：

```
C:\Users\ユーザー名\AppData\Roaming\npm\node_modules\@modelcontextprotocol\server-brave-search\dist\index.js
```

- ファイルシステム用パス：

```
C:\Users\ユーザー名\AppData\Roaming\npm\node_modules\@modelcontextprotocol\server-filesystem\dist\index.js
```

### 2-5 設定後の再起動

設定を変更した後、アプリの再起動だけではうまく反映されない場合があります。

- **推奨**：一度パソコンを完全にシャットダウンして再起動する。

## 3. 実際の設定例

以下は、Brave SearchとファイルシステムをClaude MCPに統合するための設定例です。

**`claude_desktop_config.json` の例**:

```
{
  "mcpServers": {
    "brave-search": {
      "command": "node",
      "args": [
        "C:\\Users\\ユーザー名\\AppData\\Roaming\\npm\\node_modules\\@modelcontextprotocol\\server-brave-search\\dist\\index.js"
      ],
      "env": {
        "BRAVE_API_KEY": "XXX"
      }
    },
    "filesystem": {
      "command": "node",
      "args": [
        "C:\\Users\\ユーザー名\\AppData\\Roaming\\npm\\node_modules\\@modelcontextprotocol\\server-filesystem\\dist\\index.js",
        "C:\\Users\\ユーザー名\\Documents"
      ]
    }
  }
}
```

**注意**：

- `BRAVE_API_KEY` は適切なAPIキーに置き換えてください。
- C:のパスはご自身の格納先に置き換えてください。
- 設定ファイルを保存後、パソコンを再起動してください。

ぜひ、こちらを参考にして、Windowsユーザーの方はClaude MCPを導入してみてください。

## 4. ClaudeのMCP活用事例：農業×生成AIの最新動向調査

ClaudeのMCP 機能を活用して、農業分野における生成AIの最新動向を包括的に調査しました。MCPの特徴である複数のAPI呼び出しを組み合わせることで、Brave検索による情報収集から、データの構造化、そしてCSVファイルでのレポート作成までを実行できました。

### 具体的な活用手順

1. Brave検索による情報収集：農業×AI分野の最新事例を、信頼性の高い情報源から効率的に収集
2. データの構造化：8つの主要カテゴリーに分類し、実装事例、期待効果、市場予測を整理
3. レポート作成：収集した情報をCSVファイル形式で出力し、再利用可能な形式で保存

![](https://assets.st-note.com/img/1733184323-wBgAurzdRa4lQPiUS3FHe08I.png?width=1200)

Claudeで図解に

調査の結果、農業分野におけるAI活用は急速に進展していることが明らかになりました。注目すべき点として、精密農業支援による収穫量の最大20%向上、水資源使用量の30-50%削減などの具体的な効果が確認されています。また、農業AI市場は2028年までに47億ドル規模への成長が予測されており、特に再生型農業分野では2030年までに2000億ドル規模の市場形成が見込まれています。

※動画解説はこちら

[https://www.youtube.com/embed/JWtFhg24rPQ?rel=0](https://www.youtube.com/embed/JWtFhg24rPQ?rel=0)

## 5. まとめとおすすめリソース

Claude MCPの導入にはいくつかの落とし穴がありますが、この記事で紹介したポイントを押さえれば、スムーズに環境を構築できるはずです。

**ポイントの振り返り**：

1. 設定ファイルは新規作成が必要。
2. Node.jsのバージョンは最新でなく、安定した推奨版を使用。
3. パスの記述は`\`を使用し、正確に指定。
4. 再起動はマメに。

**おすすめリソース**：

- [Node.js公式サイト](https://nodejs.org/)
- [Zenn記事: Node.jsの設定](https://zenn.dev/)
- [Claude公式ドキュメント](https://www.anthropic.com/)

Claude MCPは複数の情報源からのデータ収集、構造化、そしてレポート作成までの一連のプロセスを自動化できる点は、今後のAIエージェント活用の可能性を大きく広げるものと言えるでしょう。

[#情報](https://note.com/hashtag/%E6%83%85%E5%A0%B1)

[#生成AI](https://note.com/hashtag/%E7%94%9F%E6%88%90AI)

[#データ](https://note.com/hashtag/%E3%83%87%E3%83%BC%E3%82%BF)

[#設定](https://note.com/hashtag/%E8%A8%AD%E5%AE%9A)

[#LLM](https://note.com/hashtag/LLM)

[#Claude](https://note.com/hashtag/Claude)

[#mcp](https://note.com/hashtag/mcp)

## いいなと思ったら応援しよう！