---
title: obsidian-link-embed はいいぞ！【Obsidian プラグイン紹介】｜かいりん
source: https://note.com/kairin__/n/nf046727f5a47
author:
  - "[[note（ノート）]]"
published: 2024-03-02
created: 2025-03-09
description: 出来がめちゃくちゃ良い  obsidian-link-embedは、ObsidianにURLリンクをいい感じに埋め込むためのプラグインだ  デフォルト状態で普通に使っててもObsidianにURLを書くと、ちょうどいい感じにハイパーリンクを自動的に貼ってくれる。これはこれでいい感じだ！ ちょうどいいハイパーリンク でも例えば note だったらこんな感じに  Notion だったらこんな感じにリンクにOGPを埋め込んでくれるッ！ Notionのリンク埋め込み機能 URLだけでは物足りないが情報を自分で書くのはめんどくさい自分にとって、URL埋め込み機能は重用することが多い、しかしOb
tags:
  - obsidian
---
obsidian![見出し画像](https://assets.st-note.com/production/uploads/images/132643029/rectangle_large_type_2_2b318c88942d90db94becc50cee62afd.png?width=1200)

[かいりん](https://note.com/kairin__)

2024年3月2日 12:31 フォローしました

## 出来がめちゃくちゃ良い

obsidian-link-embedは、ObsidianにURLリンクをいい感じに埋め込むためのプラグインだ

デフォルト状態で普通に使っててもObsidianにURLを書くと、ちょうどいい感じにハイパーリンクを自動的に貼ってくれる。これはこれでいい感じだ！

![画像](https://assets.st-note.com/img/1709346456844-sEkYHqjSO5.png)

ちょうどいいハイパーリンク

でも例えば note だったらこんな感じに

Notion だったらこんな感じにリンクにOGPを埋め込んでくれるッ！

![画像](https://assets.st-note.com/img/1709346335165-z0kTHorKBm.png?width=1200)

Notionのリンク埋め込み機能

URLだけでは物足りないが情報を自分で書くのはめんどくさい自分にとって、URL埋め込み機能は重用することが多い、しかしObsidianにはその機能がない

Obsidianでもできたらいいのにな～無理だろうな～でも一応プラグインを探してみるか～**あｔｔｔｔｔｔｔｔｔｔった！！！  
**（Obsidianは単体のアプリとしても神だがエコシステムも神だマジで）

> 例によってインストールする時は普通にObsidianからSettings > Community plugins > Browse > "link-embed" とか入力して検索してくれよな

「できるよ」と「質がよくて常用したくなるよ」の間には高い壁がそびえているのがこの世の常。だがしかし出来もめちゃくちゃよかったぞ

![画像](https://assets.st-note.com/img/1709350171882-OV6bbPUlgO.png?width=1200)

めちゃくちゃよい出来のembed

動作の雰囲気は、百聞は一見に如かずとりあえず７秒の動画を見てくれ

  

以下、何がいい感じなのか念のため文字でも軽く触れておく

## 動作が軽い

動作が非常に軽い！リンクを埋め込んでも、Obsidianの動作が遅くなることはない！

## fetchのロジックが賢い

OGP情報、サムネイル画像・ページタイトル・概要、URL……をいい感じの見た目で埋め込んでくれる。他の画面要素とも自然に調和するぞ！

## embedの見た目を完全にコントロールできる

プラグインが入ってるといい感じの見た目だが、実態としては超シンプルなテキストデータだ

```python
\`\`\`embed
title: "obsidian-copilotが快適すぎてHotkeyをアサインするついでに既存のHotkey一覧を整理したメモ｜かいりん"
image: "https://assets.st-note.com/production/uploads/images/131959013/rectangle_large_type_2_e87349d7f9fa132008bd03df6f9a71d0.png?fit=bounds&quality=85&width=1280"
description: "アプリ内で表示させればいいだけなんだけど、せっかくだから文字列として取得したくなった。プレーンテキストとして一発でエクスポートする手段はなさそうだったので 設定画面からHotkey一覧を表示 Windowsの画面からテキスト抽出機能で文字列をコピー Windows + Shift + T Obsidianにペースト obsidian-copilotで修正 Fix grammar and spelling of selection Model: Gemini Pro 目視による検品と微修正 obsidian-copilotで修"
url: "https://note.com/kairin__/n/n54c60c78e39d"
\`\`\`
```

fetch先との接続が失敗したりfetchされてきた画像や文章が気にくわなくても、embed内のコードを軽くいじるだけで、見た目を思い通りに変更することができるぞ！

![画像](https://assets.st-note.com/img/1709348677620-EoTbDAQ6MF.png?width=1200)

例えばこんな感じだ

これができるの、意外と珍しいんじゃないかな？（例えばNotionではできないと思われ）

  

## 神プラグイン

obsidian-link-embedは、まさに神プラグイン。動作が軽くてfetchのロジックが賢く埋め込みの見た目を完全にコントロールすることができる。Obsidianユーザーならぜひ試してみてくれよな！！！

  

## Obsidian関連note

  

## いいなと思ったら応援しよう！

- [

#プラグイン

](https://note.com/hashtag/%E3%83%97%E3%83%A9%E3%82%B0%E3%82%A4%E3%83%B3)
- [

#Obsidian

](https://note.com/hashtag/Obsidian)