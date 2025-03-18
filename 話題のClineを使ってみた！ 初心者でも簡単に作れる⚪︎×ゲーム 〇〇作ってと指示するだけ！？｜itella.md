---
title: 話題のClineを使ってみた！ 初心者でも簡単に作れる⚪︎×ゲーム "〇〇作って"と指示するだけ！？｜itella
source: https://note.com/itella/n/nbb373476c73a
author:
  - "[[note（ノート）]]"
published: 2025-02-25
created: 2025-03-09
description: はじめに  こんにちは！ 以前会社の研修でCline(クライン)というエージェント型の開発ツールについて触れました！ 今回はClineの紹介と⚪︎×ゲーム(三目並べ)を作っていきます！  Clineとは？  Cline(クライン)は、Visual Studio CodeやCursorなどで使用できるAIエージェント型の拡張機能です。 普通の言葉で「こんなプログラムを作りたいな」と伝えるだけで、AIが理解して必要なコードを作ってくれます！ 他にも既存のコードを修正したりすることができたり、コード修正だけではなく自動的にバグを修正をしてくれたり、作ったプログラムのテストをAIがしてくれるん
tags:
  - プログラミング
  - cline
---
![見出し画像](https://assets.st-note.com/production/uploads/images/176280661/rectangle_large_type_2_6d59687ef538293ea8c202ee1cd7f152.png?width=1200)

[itella](https://note.com/itella)

2025年2月25日 11:09 フォローしました

## はじめに

こんにちは！  
以前会社の研修で**Cline(クライン)**というエージェント型の開発ツールについて触れました！  
今回はClineの紹介と⚪︎×ゲーム(三目並べ)を作っていきます！

## Clineとは？

Cline(クライン)は、Visual Studio CodeやCursorなどで使用できるAIエージェント型の拡張機能です。  
普通の言葉で「こんなプログラムを作りたいな」と伝えるだけで、AIが理解して必要なコードを作ってくれます！  
他にも既存のコードを修正したりすることができたり、コード修正だけではなく自動的にバグを修正をしてくれたり、作ったプログラムのテストをAIがしてくれるんです！

Clineは使用するAIプロバイダーに応じて料金が変動する**従量課金制**です。  
Geminiの無料プランを使うことで無料で始めることも可能です！

## 🌟 Clineのポイント

- VSCodeやCursorで使える便利な拡張機能
- 無料で始められる（Geminiの無料プランを使用）
- 日本語で指示を出せる
- コードの生成からテスト、バグ修正までAIがサポート

##  Clineのはじめかた

### GeminiのAPIキーを取得する

Geminiの無料プランを使う方は、GeminiのAPIキーを取得しましょう。  
  
無料プランのためリクエスト数やトークン数に制限があると思います。  
⚠️ **連続して使用すると制限にかかってしまうのでお気をつけください。**

[Google AI studio](https://aistudio.google.com/prompts/new_chat)にアクセスします。  
今回はAPIキーを取得するので「**Get API Key**」をクリックします。

![画像](https://assets.st-note.com/img/1740117672-ftE93Z5vMjnX0HYehdR4C8uP.png?width=1200)

「**APIキーを作成**」をクリックすると、APIキーが発行されます。  
発行したAPIキーはあとで使用します。

![画像](https://assets.st-note.com/img/1740122468-Xq81PbFcSTMpW9IuYRxDoGfw.png?width=1200)

### Clineのインストール

**⚠️** [**Cursor**](https://www.cursor.com/ja)**または**[**VSCode**](https://azure.microsoft.com/ja-jp/products/visual-studio-code)**の環境をお持ちでない方**は公式サイトからダウンロードしましょう！

CursorまたはVSCodeを起動させ、拡張機能で「Cline」と検索しインストールします。

![画像](https://assets.st-note.com/img/1740122770-EhuIANom608ZzfwXygCGxHcj.png?width=1200)

インストールが完了すると、左側のメニューに「Cline」のアイコンが表示されます。  
ピンマーク📌をクリックすることでメニューに固定することも可能です。

![画像](https://assets.st-note.com/img/1740122911-H891R3yuM4DUri60FvC5hkJx.png)

次にClineの設定をします。  
以下のように設定できたら「**Done**」をクリックします。  
・API Provider：Google Gemini  
・Gemini API Key：発行したAPIキーを設定  
・Model：gemini-2.0-flash-lite-preview-02-05  
・Custom Instructions：英語を使わないで日本語を使って  
　→日本語を使う設定をします

![画像](https://assets.st-note.com/img/1740123962-YuPDtaF8LBE4e9QdwNWRVOzS.png)

タブの「New Task」をクリックすると、下の方にチャット欄が表示されます。チャット欄の下にモデルが表示されるので、設定したモデル(gemini)になっているか確認しましょう。

![画像](https://assets.st-note.com/img/1740124445-7JlUqI6iDgz2Fn8ArmOWTHNM.png)

ClineではAIが「このコマンドを実行しますか？」などユーザーに提案して、実行していいか、作業を進めていいか確認をしてくれます。  
**Auto-approve**のチェックマークを有効にすることで、権限を与えることができ承認作業をスキップして勝手にタスクを進めてくれる機能です。

## Clineを触ってみる

実際にClineを触ってみましょう！

チャット欄に以下のように指示するだけで、⚪︎×ゲーム(三目並べ)の実装を始めてくれます。

> Next.jsで〇×ゲーム（Tic-Tac-Toe）を作成してください。

![画像](https://assets.st-note.com/img/1740127214-YU5WetahXj61LiRucdAwFDqf.png)

⚪︎×ゲーム(三目並べ)を実装した後に、ブラウザでページを開いてくれましたが、「接続できません」という表示になったため、プロジェクトフォルダを開いて、「Next.jsで〇×ゲーム（Tic-Tac-Toe）を作成してください。」と指示すると、原因を調べて修正してくれました。  
  
「接続できません」は解決できましたが、エラーが出ていたのでブラウザに表示されているエラーを全てコピーして、Clineのチャットにエラーの内容を貼り付け実行すると・・・

![画像](https://assets.st-note.com/img/1740128009-VWnCieb2Pf50lOMN6B74dgxh.png?width=1200)

エラーが修正され⚪︎×ゲームのページが表示されプレイできました👏✨

![画像](https://assets.st-note.com/img/1740128017-IO6QyKnYL540RDjbxhzSqw7i.png?width=1200)

## さいごに

今回はClineを使って⚪︎×ゲーム(三目並べ)を作成してみましたが、いかがだったでしょうか？  
「こんなアプリ作りたい！」という発想があれば、Clineですぐに作成できます！  
「〇〇して」と伝えるだけで、あっという間にゲームができるなんてすごくないですか😳！？  
  
特に初心者の方には、アプリ開発の入り口として最適かもしれません。  
ちょっとでも興味がある！という方は、ぜひ試してみてください！

最後までありがとうございました。

引用元ブログ

[**AIによる開発を体験してみよう（Clineを使った開発）** *zenn.dev*](https://zenn.dev/chameleonmeme/articles/1c09e8f856c36b)

  

  

  

  

## いいなと思ったら応援しよう！

- [

#AI

](https://note.com/hashtag/AI)
- [

#ゲーム

](https://note.com/hashtag/%E3%82%B2%E3%83%BC%E3%83%A0)
- [

#cline

](https://note.com/hashtag/cline)
- [

#開発ツール

](https://note.com/hashtag/%E9%96%8B%E7%99%BA%E3%83%84%E3%83%BC%E3%83%AB)
- [

#初心者におすすめ

](https://note.com/hashtag/%E5%88%9D%E5%BF%83%E8%80%85%E3%81%AB%E3%81%8A%E3%81%99%E3%81%99%E3%82%81)