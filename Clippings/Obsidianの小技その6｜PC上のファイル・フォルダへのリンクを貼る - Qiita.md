---
title: "Obsidianの小技その6｜PC上のファイル・フォルダへのリンクを貼る - Qiita"
source: "https://qiita.com/hann-solo/items/992e93a417ef4e2ba536"
author:
  - "[[Qiita]]"
published: 2022-01-05
created: 2025-03-19
description: "はじめにつねに開きっぱなにしているMarkdownメモツールObsidian。1年ぐらい使ってみたので、ストレスフリーに近づける、いいかんじの小技をご紹介してみたいとおもいます。ファイルへのリン…"
tags:
  - "clippings"
---
この記事は最終更新日から3年以上が経過しています。

[@hann-solo(hann solo)](https://qiita.com/hann-solo)

## Obsidianの小技その6｜PC上のファイル・フォルダへのリンクを貼る

最終更新日 投稿日 2022年01月05日

## はじめに

つねに開きっぱなにしているMarkdownメモツール[Obsidian](https://obsidian.md/)。1年ぐらい使ってみたので、ストレスフリーに近づける、いいかんじの小技をご紹介してみたいとおもいます。

## ファイルへのリンクを貼る

Obsidianは「リンクを貼りまくる」ことで便利になるツールです。なかでもPCに保存しているファイルにリンクを貼れて、これはめちゃめちゃ便利です。

- たとえば、PDFファイルを貼っておくと、クリックするとファイルが開きます
- さらには、フォルダも貼れて、そのばあいはクリックするとフォルダが開きます
- 文書内への画像の貼り込みにも使えます

リンクの形式は

Copied!

```markdown
[表示テキスト](file://フルパス)

# 念を入れるならカッコをつけて
[表示テキスト](<file://フルパス>)
```

で、たとえばPDFの場合：

Copied!

```markdown
[soramame](file:///Users/username/Desktop/soramame.pdf)
```

フォルダの場合：

Copied!

```markdown
[211201_退避](file:///Users/username/Desktop/211201_退避)
```

みたいになります。

画像ファイルへのリンクを

Copied!

```markdown
![soramame](file:///Users/username/Desktop/soramame.png)
```

と書いておくと、プレビューモードでは文書内で画像が見えます。

[![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F184128%2Ff8fc8302-5429-27cc-daf8-88673b4be44b.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=afba04c7f2b5cddd13884d7987ec1d66)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F184128%2Ff8fc8302-5429-27cc-daf8-88673b4be44b.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=afba04c7f2b5cddd13884d7987ec1d66)

## フルパスのとりかた

ファイルのフルパスを取るのがわからん！めんどくさい！とおもうんですけども、macOSの場合だと、ファイルを右クリック→optionキー押すと`xxxxのパス名をコピー`とすれば簡単に取れます。

Windowsは、エクスプローラに表示されているとおもいます。

## さらにラクする方法

わたしはもう右クリックもoptionキーを押すのもめんどうくさいし、`[xxxx](<file://>)`と書くのもめんどうなので、Automatorで小さなツールをつくりました。

参考：[Obsidianで便利なローカルファイルへのリンクを、Automatorに作成してもらうと楽ちんだなあ](https://qiita.com/hann-solo/items/5537e54704db48696f80)

これをクイックアクションに追加しているので、アイコン（mdStyleLink）をワンクリックで、クリップボードにMarkdownのリンク形式がコピーされます。

[![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F184128%2F57d457ae-7ffe-b267-ecff-2bed2748f05b.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=2cef58c12e4f30f5dffb65ff0db765a2)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F184128%2F57d457ae-7ffe-b267-ecff-2bed2748f05b.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=2cef58c12e4f30f5dffb65ff0db765a2)

↓

Copied!

```markdown
# ペーストすると
[SS 2022-01-05 18.47.25.png](<file:///Users/username/Desktop/SS 2022-01-05 18.47.25.png>)
```

このミニツールのおかげで、わたしのノートは、リンク貼りまくりになっています。情報のソースがどこだったかを、覚えておく必要がなくなり、Obsidianのノートに貼っておくだけで済みます。記憶力がもともと弱いので、こういうことはツールが代行してくれると、脳に余白ができてたいへんに助かっています。

## おわりに

Obsidianのリンクを大別すると、３つになります。

| 種類 | 形式 |
| --- | --- |
| 内部リンク | `[[xxxx]]` |
| 外部リンク | `[xxxx](https://yyyy)` |
| ファイルリンク | `[xxxx](<file://フルパス>)` |

さいごのファイルリンクは、[Obsidianのヘルプにも載ってはいる](https://publish.obsidian.md/help-ja/%E9%AB%98%E5%BA%A6%E3%81%AA%E3%83%88%E3%83%94%E3%83%83%E3%82%AF/Obsidian+URI%E3%81%AE%E5%88%A9%E7%94%A8)ものの、あまり詳しく書いていないので見逃されがちです。書いていることも、なんだかよくわかんないし。

しかしながらObsidianを思考支援ツールとして使うにあたって、必須のリンクではないかとおもっています。

次回は、プレビュー文書に画像を貼る小技を、もう少し紹介できればなとおもっています。

### ご参考

[Obsidian｜使いかたとコツ（目次）](https://qiita.com/hann-solo/items/ac8fa75394813e8adcf4)

[32](https://qiita.com/hann-solo/items/992e93a417ef4e2ba536/likers)

26

[0](https://qiita.com/hann-solo/items/#comments)