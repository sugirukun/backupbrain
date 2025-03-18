# Zenn完全に理解した #Zenn - Qiita

カテゴリー: Qiita Zenn note, 情報技術
URL: https://qiita.com/unsoluble_sugar/items/558a11b455d042d648d6

この記事は「[完全に理解したTalk Advent Calendar 2020](https://qiita.com/advent-calendar/2020/easyeasy)」15日目の投稿記事です。

# 話題のZennを触ってみた

巷で話題の[Zenn](https://zenn.dev/)という技術情報共有サービスを先月から触っています。

[Zenn｜エンジニアのための情報共有コミュニティ](https://zenn.dev/)

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F6380%2F5037ee54-2194-3fa9-9a0a-c3b64b0442b9.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=84417ad216fbb0b22b2fc5a33fa61e30)

Qiitaアドベントカレンダーでもリンク先記事がZennで書かれているケースがチラホラ見受けられたり、はてブのホットエントリーにも上がってくることが増え、気になっている方もいらっしゃるのではないかと思います。

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F6380%2Fd5baa432-bab8-f7fd-a791-2f1a0961a84f.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=729fca3bbf1cd3d5446de908daf68c01)

かくいう筆者も遅ればせながら、1ヶ月程度Zennで記事を書いてみて「Zenn完全に理解した」状態になりましたので、所感をザッと書き残してみます。

**2021年2月1日追記：クラスメソッド株式会社に買収されたとのこと**

[クラスメソッド、技術情報共有サービス「Zenn」の買収に関する契約を締結〜誰かのために、自分のために知見を共有するプラットフォームの開発を加速〜 | ニュース | クラスメソッド](https://classmethod.jp/news/20210201-zenn/)

# Zennとは？

まずはZennの概要紹介です。

> 
> 
> 
> Zennはエンジニアのための新しい情報共有コミュニティです。
> 
> 誰かのために、自分のために知見を共有しましょう。
> 
> [Zennとは？｜エンジニアのための情報共有コミュニティ](https://zenn.dev/about)
> 

ここだけ読むと「Qiitaと何が違うん？」と思いますよね。自分もはじめはそう思っていたのですが、色々と既存サービスとは異なる部分があります。

## 情報を発信するエンジニアが対価を得られる仕組み

例えばnoteのように知見の対価として著者を金銭的にサポートできたり、本を執筆して販売することができたりします。

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F6380%2F2095870a-a205-73f5-50e6-378795ffd8c3.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=92c659f9575dd09c9aefcae2dc705c9f)

コンセプトの一貫として、**情報発信をするエンジニアが対価を得られるような仕組み**が備わっています。

> 
> 
> 
> エンジニアには学びやアイデアを、他のエンジニアのためにオープンに共有し、助け合う文化があります。
> 
> しかし、地道に有益な知見を発信し、コミュニティに貢献しているエンジニアが、必ずしも対価を得られているとは限りません。広告だらけの情報共有サービスに自分の知見を投稿し、自分のもとには1円も入らないのは果たして健全なのでしょうか。
> 

本の価格設定は無料～5,000円までとなっており、一部のチャプターやすべてを無料公開することもできます。電子書籍のような形態ではなく、Web上のリーダーで体系的に閲覧できるチャプター方式です。

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F6380%2Ff2fec1cc-ce5b-aa4d-23b9-9350043f8687.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=e3e1ffca9d0aec707e8e0eddaaa1c72b)

noteでも技術系の記事が有料販売されていたりもしますし、スマホにも最適化されたデザインになっているので、こういったスタイルでも読みやすいのかなと感じました。

ちなみにZennでは記事の有料販売はできず、サポートのみ受付可能となっています。記事と本の切り分けについて、公式では以下のように言及されています。

> 
> 
> 
> 記事を有料販売できない理由は、気軽に知見をシェアし、気軽に情報収集できるようにするためです。ちょっとした調べ物をしているときにヒットした記事が「ここからは購入者のみ読むことができます」と途中で終わっていたらストレスに感じると思います。そのため、本だけを有料販売できるようにしています。
> 
> [Zennの本とは｜Zennで本を執筆する！本の作成マニュアル](https://zenn.dev/zenn/books/how-to-create-book/viewer/about)
> 

金銭的インセンティブのあるWebサービスでは、いわゆる情報弱者を食い物にする輩が現れる懸念もありますが、サービスリリース当初より強いエンジニアが参戦していることもあり、いまのところそのような傾向が顕著に見られる気配はなさそうです。

実際、無料でとんでもないクオリティの本を書かれている方もおりまして…この土壌で有料本を出してウハウハとなる方がどの程度出てくるかは、正直未知数という印象です。

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F6380%2F87c4d927-3ee9-bbcc-5d53-63cca9733d2f.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=98d37842ef6c7bcc15d468a6f60cf22f)

一方で、良質な記事や応援したい人に投げ銭感覚でサポートしていく文化が浸透すれば、記事や本を書く側のモチベーションも少しづつ上がっていくことでしょう。願わくば、無理なく健全な形で著者・読者間の好循環が生まれることを期待しています。

## 最高のUX

その他の特徴を挙げると、以下のようなものがあります。

- [Markdown記法](https://zenn.dev/zenn/articles/markdown-guide)で書ける
- Tech（技術記事）/ Idea（アイデア記事）の投稿カテゴリ分けが可能
- SpeakerDeckやSlideshare、YouTube等の埋め込みができる
- スレッド形式で知見やメモをまとめられる[スクラップ機能](https://zenn.dev/zenn/articles/about-zenn-scraps)がある
- シンタックスハイライトがきれい
- 全体的なUI/UXデザインが洗練されている
- [GitHubリポジトリ連携（β版）](https://zenn.dev/zenn/articles/connect-to-github)でコンテンツ管理が可能
- 専用のCLIツールがある
- [Google Analytics連携](https://zenn.dev/unsoluble_sugar/articles/c784905997dde2ffce68)が可能
- Zenn開発者[catnose](https://twitter.com/catnose99)さんの技術力がすごい（[サルワカ](https://saruwakakun.com/)運営, [RESUME](https://www.resume.id/)開発, [etc...](https://www.resume.id/catnose99/works)）

洗練されたUI/UXのおかげなのか、記事の執筆・閲覧の体験が非常に気持ち良いんですよね。

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F6380%2F6133396d-0051-1ea9-8237-27bec48f70f4.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=9b7d76bf1b7d80177b1892758a450445)

記事投稿時に「Tech（技術記事）」「Idea（アイデア記事）」のカテゴリ選択ができる点も嬉しいです。Qiitaだとポエムがノイズになって辟易することが多いので「そういうの投げたい時はIdeaへ」といった選択肢があらかじめ用意されているのは好印象。見る側のストレスも軽減されますね。

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F6380%2Ff9b540ca-02af-4809-417d-46597918d615.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=22a74c41846a238fa4fb56ba9e1ac382)

加えて、GitHubリポジトリ連携やスライドの埋め込み対応、気軽に投稿できるスクラップ機能などなど。かゆいところに手が届くという感じ。いたれりつくせりです。

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F6380%2Fc4326063-e8d9-53e8-5ea6-bbd54d35dfb4.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=208831a7417cf1ff4cd1a0dd76ce76bb)

記事のアイキャッチ設定が絵文字で統一されているのも可愛い。

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F6380%2F97870d74-c0d8-09f2-3fa3-3da5b6d31418.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=b206258c1d5e2f0fc08e3b6cdece06ae)

そんな感じで語りたいことは多々あるのですが、中でも特筆すべき「GitHubリポジトリ連携」機能について、本記事で紹介したいと思います。

# ZennのGitHubリポジトリ連携

ZennはGitHubリポジトリと連携して記事の管理を行うことができます。

- [Zennのコンテンツ作成ガイド](https://zenn.dev/zenn/articles/editor-guide)
- [GitHubリポジトリでZennのコンテンツを管理する](https://zenn.dev/zenn/articles/connect-to-github)

快適なWebエディターもあるのですが、ZennとGitHubリポジトリを連携すると、ローカルの好きなエディターで投稿コンテンツの作成・編集ができるようになります。

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F6380%2F61f4f925-d5d1-d791-767b-418ad0e06062.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=e347bec0b340765a3a69b037d9dbbc1a)

## git管理＆自動デプロイ

連携後は投稿コンテンツの作成・更新をすべてリポジトリ内で行うことになります。ローカルで記事を書いて対象ブランチに変更をプッシュすると、Zennへ自動的にデプロイされるといった仕組みになっています。

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F6380%2Fedfba356-d24c-35ad-bd8e-76e13cf3701f.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=c94f17e929ad168361bc73ad7d6acf85)

連携手順は、Zenn公式の解説記事を見ればサクッと済みます。

- [GitHubとの連携手順](https://zenn.dev/zenn/articles/connect-to-github#github%E3%81%A8%E3%81%AE%E9%80%A3%E6%90%BA%E6%89%8B%E9%A0%86)

## CLIツールも充実

また、ローカルでの執筆時、スムーズにマークダウンファイルの作成をしたりコンテンツをプレビューすることができる「[Zenn CLI](https://github.com/zenn-dev/zenn-editor)」というNode.js製のツールも用意されています。

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F6380%2Fb5d1b515-0f6c-5e3e-dcc6-92a912eb1143.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=5b39103c3c5ac362c2147831aea61370)

こちらもZenn公式の解説記事がありますので、サクッと導入しちゃいましょう。[Node.js](https://nodejs.org/ja/)がインストールされた環境であれば、MacでもWindowsでも同じ手順で導入できました。

- [Zenn CLIをインストールする](https://zenn.dev/zenn/articles/install-zenn-cli)
- [Zenn CLIで記事・本を管理する方法](https://zenn.dev/zenn/articles/zenn-cli-guide)

執筆時によく使うコマンドだけ、ここにメモしておきます。

### 記事のmdファイル作成コマンド

以下コマンドで新規記事のmdファイルが生成されます。

```
$ npx zenn new:article

```

作成されるmdファイル名は、ユニークな[スラッグID](https://zenn.dev/zenn/articles/what-is-slug)が割り振られます。

> 
> 
> 
> [[]]
> 

ファイル内の先頭には、タイトルやトピックス(タグ)等のメタ情報が入ります。

```
---
title: "" # 記事のタイトル
emoji: "🌟" # アイキャッチとして使われる絵文字（1文字だけ）
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [] # トピックス（タグ）["markdown", "rust", "aws"]のように指定する
published: false # 公開設定（falseにすると下書き）
---
ここから本文を書く

```

必要なメタ情報を入力して、本文を書いていくという流れですね。

### 記事のプレビューコマンド

以下コマンドを叩くとlocalhostで記事のブラウザプレビューができます。

```
$ npx zenn preview

```

記事ファイルの変更内容がホットリロードで即時反映されるので、プレビュー画面を見ながらの執筆も快適です。

記事ファイルはマークダウン形式ですので、VSCode等であればマークダウンプレビューを使うことで、エディタ単独で編集ファイルとプレビュー表示を左右に並べることも可能です。

Qiitaと同じような感覚で書けますね。

### 画像について

GitHub連携時の画像挿入に関しては、Zennダッシュボードの[画像アップロード機能](https://zenn.dev/dashboard/uploader)を使う必要があります。

こちらに画像をアップして、記事内で使用する画像URLの含まれたタグをコピーします。

- [📷画像のアップロード | Zenn](https://zenn.dev/dashboard/uploader)

残念ながらこの画面でアップした画像URLは、画面を切り替えてしまうと辿れなくなってしまうようです。

すでにZenn上にアップした記事やスラッグ内の画像URLであればそのまま使えます。自分はスクラップに作業ログとして画像をアップしながらメモしているので、記事化する際はスクラップから画像URLを引っ張ってくる形で対応しています。

あとから必要になる画像もスクラップに貼り付けてしまえば、画像を再アップせずコピペできますし作業内容との紐付けもできますからね。

### 埋め込み系のタグについて

こちらも画像と同じく、ローカルのエディタのみでの対応がやや難しいです。

- [ZennのMarkdown記法 - コンテンツの埋め込み](https://zenn.dev/zenn/articles/markdown-guide#%E3%82%B3%E3%83%B3%E3%83%86%E3%83%B3%E3%83%84%E3%81%AE%E5%9F%8B%E3%82%81%E8%BE%BC%E3%81%BF)

ZennのMarkdown記法を完全に覚え切れていないので、適当なスクラップ投稿で埋め込みエディタのダイアログを開いて、そこからタグ生成してコピペする方法で対処しています。

タグの基本構成としては、サービス名にURLやKey、IDを組み合わせたもになっているので、ある程度書き慣れたらノールックでいけるかもですね。

[CodePen](https://codepen.io/)や[CodeSandbox](https://codesandbox.io/s)などの外部サービスにも対応しているので、サンプルコードだけでなく、その場で表示が試せる記事を書くこともできます。

QiitaでもCodePenの埋め込みは可能ですが、[Embed取得までの手順が若干面倒](https://qiita.com/fumu238/items/f73274aa1a188eb15794)です。

```
<p class="codepen" data-height="265" data-theme-id="light" data-default-tab="css,result" data-user="elsemeow" data-slug-hash="mdrrZPe" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="The Hidden Gifts 🎁">
  <span>See the Pen <a href="https://codepen.io/elsemeow/pen/mdrrZPe">
  The Hidden Gifts 🎁</a> by Maxim Belov (<a href="https://codepen.io/elsemeow">@elsemeow</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

```

Zennの場合はタグにページURLを挿入するだけ。

```
@[codepen](https://codepen.io/elsemeow/pen/mdrrZPe)

```

他サービスの埋め込みも1行。シンプルです。

# Zennはいいぞ

こんな感じでZennとGitHubリポジトリを連携させて、何本か記事を書いております。後半に記載したようなローカルのみで完結しない作業が一部あるものの、いまのところ概ね快適です。

なんといってもWeb上で途中まで書いていた記事が吹っ飛ぶといった不慮の事故が減るのは大きなメリットです。心配ならこまめにgitコミットしておけば、バックアップ体制も抜かり無いでしょう。切り戻しやブランチ切ってレビュー＆プルリクマージなどもできますからね。

もちろん他サービスでも自分でコンテンツ管理すれば似たようなことは可能ですが、サービス自体に連携機能が組み込まれているのは非常にありがたいです。

## 著者側の視点

ローカルで好きなテキストエディタを使って記事を書けるだけでなく、様々な可能性を感じさせてくれるのがZennの魅力ですね。

例えばリポジトリを共有して、複数人による記事の共同編集や本の執筆を行なったり「CIツールを噛ませた投稿連携などもできそうだなぁ」といった、エンジニアの創意工夫の見せ所が溢れるようなサービスではないかと感じています。

最近は[スクラップ](https://zenn.dev/unsoluble_sugar/scraps)にやりたいことや作業ログを書き殴って、ある程度情報がまとまったら記事化するといった流れで運用を回しています。ツイ廃なので延々とスクラップに垂れ流しがち。

これが自分の記事作成フローとして非常に馴染んでおり「Zennマジ最高だな…」と思える大きな要因のひとつとなっています。

## 読者側の視点

読者側の視点で言えば、Qiitaとはまた少し違った属性のエンジニアさんが集まっていたり、記事や本の見せ方も異なるので、得られる情報が新鮮に感じますね。

Zenn内の回遊導線もうまく作られており、訪れるたび新しい発見ができてワクワクします。[開発ロードマップ](https://github.com/zenn-dev/zenn-roadmap/projects/1)や[チェンジログ](https://zenn.dev/changelog)を眺めてみると、日々着実にアップデートが行われていることがわかります。

Zennのサービス全体に言えることですが、見かけだけではないサービス面の工夫が随所に見られる点がエンジニアの心を掴むポイントなのかなと思いました。

[Zenn｜エンジニアのための情報共有コミュニティ](https://zenn.dev/)

# 参考

本記事はZennで書いたスクラップと記事をベースとしています。実際にZennの記事をご覧になればQiitaとの違いを肌で感じることができますので、興味を持たれた方はぜひご参照ください。

- [Zennを完全に理解するためのメモ](https://zenn.dev/unsoluble_sugar/scraps/aaa7061659a14a313b3b)
- [GitHubリポジトリ連携を通して感じたZennの良さ](https://zenn.dev/unsoluble_sugar/articles/9c04a36a5decdb6d1b20)
- [ZennのGoogle AnalyticsトラッキングID設定方法](https://zenn.dev/unsoluble_sugar/articles/c784905997dde2ffce68)

現場からは以上です。