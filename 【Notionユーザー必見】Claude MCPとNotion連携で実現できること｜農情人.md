# 【Notionユーザー必見】Claude MCPとNotion連携で実現できること｜農情人

カテゴリー: AI, Notion, 情報技術
作成日: 2025/03/06
URL: https://note.com/noujoujin/n/nfb627bc17194

![](https://assets.st-note.com/production/uploads/images/164613229/rectangle_large_type_2_887a71c187bd63e44a94709eab2c2fea.jpeg?width=1200)

Model Context Protocol（MCP）は、Anthropic社が開発したプロトコルで、生成AI「Claude」とNotionやGithubをはじめとする、さまざまなアプリケーションを連携させることができます。

今回は、特にNotionとの連携に焦点を当て、セットアップを簡単に解説※してから実践的な活用方法まで、初心者にもわかりやすく解説します。

※詳細なセットアップ方法は前回のブログでまとめてますので、セットアップ前の方は参照いただけると幸いです。

## 1. MCPとは

Model Context Protocol（MCP）は、AIモデルと外部アプリケーションを安全かつ効率的に接続するためのプロトコルです。このプロトコルにより、ClaudeはNotionのデータベースやページを直接操作できるようになります。

## 2. Notion連携で準備するもの

- Claude Desktopアプリケーション
- Node.js（最新版は非推奨）
- Notionアカウント
- コマンドプロンプトかPowerShell
- テキストエディタ（VSCode推奨）

## 3. セットアップ手順

### 3.1 MCP Notionサーバーのセットアップ

まずは、PowerShellを管理者権限で実行して下記のコードを入力していきます。

**リポジトリのクローン**

```
git clone https://github.com/suekou/mcp-notion-server.git
```

**ビルドとリンク**

```
cd mcp-notion-server/notion
npm run build
npm link
```

### 3.2 Notion APIトークンの取得

1. [[my]]
2. 「New Integration」をクリック
3. 必要事項を入力
    - インテグレーション名
    - ワークスペースの選択
    - タイプは「Internal」を選択
4. トークンをコピー

### 3.3 設定ファイルの編集

1. `claude_desktop_config.json`を新規作成して開く※
    - Windows: `%APPDATA%\Claude\claude_desktop_config.json`
    - Mac: `~/Library/Application Support/Claude/claude_desktop_config.json`
2. 以下の設定を追加

```
{
  "mcpServers": {
    "notion": {
      "command": "node",
      "args": [
        "/path/to/mcp-notion-server/notion/build/index.js"
      ],
      "env": {
        "NOTION_API_TOKEN": "your-notion-token"
      }
    }
  }
}
```

※既にある場合は追記します。追記の流れなどは割愛しますが、不明な点がある場合は下記の手順も併せてご覧ください。

最後に、設定を反映させるために、Claudeのアプリを再起動します。

## 4. 実践的な活用事例紹介

ここからは、具体的なClaude×Notionで実現できる具体的な事例を二つ紹介していきます。

### 4.1 Claude×Notionによる情報管理の効率化

この事例では、ClaudeとNotionを連携させて情報管理を効率化する方法をNotionにまとめています。

[https://www.youtube.com/embed/9p_fO3rVkqI?rel=0](https://www.youtube.com/embed/9p_fO3rVkqI?rel=0)

具体的なアウトプットは以下の通りです：

1. 情報の構造化と整理
    - MCPを活用して、Claudeが自動的に情報を適切な構造で整理
    - 複雑な情報も、理解しやすい形式に自動変換
2. データベースの自動作成と管理
    - 必要な項目を自然言語で指示するだけでデータベースを作成
    - プロパティの自動設定と最適化
3. コンテンツの自動生成と更新
    - 概要や説明文の自動生成
    - 既存コンテンツの更新と改善
4. 実装のポイント
    - 適切なプロパティ設計
    - 効果的なタグ付けとカテゴリ分類
    - 検索性を考慮した構造化

実際のNotionへのアウトプットはこちら

 [ **Notion×ClaudeMCP | Notion**   *1. 主要機能*   [[]]  

参考動画: [Claude×Notionで実現できることをNotionにまとめ](https://www.youtube.com/watch?v=9p_fO3rVkqI)

### 4.2 web3調査のデータベース化

次に、マニアックな調査であるweb3技術を活用したReFiについて、ネットから検索して情報をデータベース形式で整理し、効率的に管理する方法を紹介します：

[https://www.youtube.com/embed/PudElhdOAuU?rel=0](https://www.youtube.com/embed/PudElhdOAuU?rel=0)

**「対話でわかる！ReFiのしくみ」のサマリー**まずは、身近な対話形式でReFi（Regenerative Finance）の基本概念を解説します：

 [ **小学生と学ぶ！クリマDAOのReFiってなんだろう？ | Notion**   *こんにちは！今日は地球の未来のために頑張っている「クリマDAO」というグループの活動について、みんなで楽しく学んでいきまし*   [[]]  

「ReFiとは、お金の力で地球環境を再生・修復する新しい金融の仕組みです。従来の金融が利益追求を主目的としていたのに対し、ReFiは環境保護や社会貢献と経済活動を両立させることを目指しています。特に、ブロックチェーン技術を活用して、環境保護活動を透明性高く、効率的に進められる点が特徴です。」

先生と生徒の対話を通じて、複雑なReFiの概念を、環境活動への投資や、カーボンクレジットの仕組みなど、具体例を交えながら分かりやすく説明しています。

**「ReFiプロジェクト事例集」のサマリー**

このデータベースでは、実際のReFiプロジェクトを体系的に整理しています：

 [ **ReFiプロジェクト事例集 | Notion**   *Made with Notion, the all-in-one connected workspace with pub*   [[]]  

このデータベースでは、実際のReFiプロジェクトを体系的に整理しています。主な事例として：

1.Flow Carbon：

- カテゴリ：環境保護
- 特徴：ブロックチェーンを活用した透明性の高いカーボンクレジット取引

2.Celo：

- カテゴリ：コミュニティ支援
- 特徴：モバイル中心のブロックチェーンプラットフォーム

3.Regen Network：

- カテゴリ：持続可能な農業
- 特徴：生態系の健全性をデジタル化・可視化

4.Toucan Protocol & KlimaDAO：

- カテゴリ：カーボンクレジット
- 特徴：実世界のカーボンクレジットをブロックチェーン上で効率的に取引

このデータベースの特徴は、各プロジェクトを「カテゴリ」「主な取り組み」「特徴」という観点で整理し、ReFiの実践例を俯瞰的に理解できる構成になっています。

参考動画: [web3関連の調査と解説をNotionにDB形式でまとめ](https://www.youtube.com/watch?v=PudElhdOAuU)

## まとめ

MCPを利用したClaudeとNotionの連携により、業務効率を大幅に向上させることができます。基本的な設定さえ完了すれば、直感的な操作で多くの作業を自動化できます。実践事例で示したように、適切に活用することで、情報管理や知識の体系化を効率的に行うことが可能です。

ぜひ、この記事を参考に、あなたの作業環境をより効率的にしていってください。

[#Claude3](https://note.com/hashtag/Claude3) [#Notion](https://note.com/hashtag/Notion) [#MCP](https://note.com/hashtag/MCP) [#Web3](https://note.com/hashtag/Web3) [#ReFi](https://note.com/hashtag/ReFi) [#ブロックチェーン](https://note.com/hashtag/%E3%83%96%E3%83%AD%E3%83%83%E3%82%AF%E3%83%81%E3%82%A7%E3%83%BC%E3%83%B3) [#AIツール連携](https://note.com/hashtag/AI%E3%83%84%E3%83%BC%E3%83%AB%E9%80%A3%E6%90%BA) [#NotionTips](https://note.com/hashtag/NotionTips) [#生成AI活用](https://note.com/hashtag/%E7%94%9F%E6%88%90AI%E6%B4%BB%E7%94%A8) [#MCPガイド](https://note.com/hashtag/MCP%E3%82%AC%E3%82%A4%E3%83%89) [#自動化](https://note.com/hashtag/%E8%87%AA%E5%8B%95%E5%8C%96) [#生産性向上](https://note.com/hashtag/%E7%94%9F%E7%94%A3%E6%80%A7%E5%90%91%E4%B8%8A) [#ナレッジマネジメント](https://note.com/hashtag/%E3%83%8A%E3%83%AC%E3%83%83%E3%82%B8%E3%83%9E%E3%83%8D%E3%82%B8%E3%83%A1%E3%83%B3%E3%83%88) [#テック初心者](https://note.com/hashtag/%E3%83%86%E3%83%83%E3%82%AF%E5%88%9D%E5%BF%83%E8%80%85) [#NotionUser](https://note.com/hashtag/NotionUser) [#Web3](https://note.com/hashtag/Web3) [#チュートリアル](https://note.com/hashtag/%E3%83%81%E3%83%A5%E3%83%BC%E3%83%88%E3%83%AA%E3%82%A2%E3%83%AB) [#ステップバイステップ](https://note.com/hashtag/%E3%82%B9%E3%83%86%E3%83%83%E3%83%97%E3%83%90%E3%82%A4%E3%82%B9%E3%83%86%E3%83%83%E3%83%97) [#実践ガイド](https://note.com/hashtag/%E5%AE%9F%E8%B7%B5%E3%82%AC%E3%82%A4%E3%83%89) [#ユースケース](https://note.com/hashtag/%E3%83%A6%E3%83%BC%E3%82%B9%E3%82%B1%E3%83%BC%E3%82%B9) [#技術解説](https://note.com/hashtag/%E6%8A%80%E8%A1%93%E8%A7%A3%E8%AA%AC)