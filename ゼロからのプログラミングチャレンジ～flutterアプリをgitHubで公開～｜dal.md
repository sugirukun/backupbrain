---
tags:
  - プログラミング
---

カテゴリー: Qiita Zenn note, flutter, github, プログラミング, 情報技術
作成日: 2025/02/26
URL: https://note.com/dandy_rhino5358/n/nab6c3eddc4a6

![](https://assets.st-note.com/production/uploads/images/173380554/rectangle_large_type_2_331c3c4ef1db5d4c5382f3e38b4b3f7e.png?width=1200)

今回は長くなりますが、flutterでアプリを作ってから、公開までを書いてみたいと思います。

アプリを作ったら

まずは、android studio上で、アプリをweb用にビルド、これは、android studioのターミナルでやってます。(作業用画面左下にターミナルボタンがあります。)

![](https://assets.st-note.com/img/1738833873-AGsMJNcoyji8lR7kr2xCvWFd.png?width=1200)

ビルド

小さくてすみません。成功すると緑色でBuildと表示されます。

![](https://assets.st-note.com/img/1738833891-45ikfQHLoryWTzbhxaZRN7YP.png?width=1200)

結果

次は、ビルドされた部分をエクスプローラーで開きます。

自分は、<user名>の次のディレクトリにandroid studioのプロジェクトのフォルダを設定しています。

ファイル

プロジェクト名のところを開いて、ここでは、pen_app5

buildのところに行きます。

![](https://assets.st-note.com/img/1738833977-ViE3xwklzFSo8IKrqZmHBGfX.png?width=1200)

フォルダ

buildを開いてwebを開きます。

![](https://assets.st-note.com/img/1738834018-aNZTypkYxilPHnvfhG51FXVM.png?width=1200)

フォルダ

開くとこんな感じ、ここにbuildした内容が付け足されます。最初からあるファイルもあるので、フォルダは絶対消さないでください！

![](https://assets.st-note.com/img/1738834037-tMAU6rd3IXTFqLjP9y7wg84Q.png?width=1200)

フォルダ

そして、ここで微調整します

indexファイル

indexファイルをソースコードをいじれるもので開きます。

![](https://assets.st-note.com/img/1738834069-KbIq9zMiyGNuFDpU83eQjWms.png?width=1200)

ファイルの内容を変更

上の<base href="/">を<base href="/プロジェクト名/">に変えます。

これをしないと、このファイルが同じディレクトリにあるdartファイルを読み込めず公開時に白紙のページになってしまいます。

![](https://assets.st-note.com/img/1738834085-LgTyAM4Zl9PapD1RSK8wmHhe.png)

変更内容

変えたらgitHubへ

![](https://assets.st-note.com/img/1738834104-Mr79LsC61ESUgdK5OQVthRoA.png?width=1200)

gitHubへ

新しいリポジトリを作成します。

![](https://assets.st-note.com/img/1738834120-T90ZLnpWPrMjGbJqYlgk4h7e.png)

リポジトリ作成

リポジトリの名前はプロジェクト名で

リポジトリのページに行くと中央部分にクイックセットアップという表示があります。

![](https://assets.st-note.com/img/1738834138-0JVqjDzZRryFK9CtpXsgAw43.png?width=1200)

ページの真ん中

ここの「既存のファイルをアップロードします」をクリックします。

するとドラックアンドドロップのページに行くので、ここで、先ほどのwebフォルダの中身をすべてドラックアンドドロップします。

![](https://assets.st-note.com/img/1738834156-Z9krIoGpsh2e3MN0RFLvuHQa.png?width=1200)

ドラッグアンドドロップ

![](https://assets.st-note.com/img/1738834174-oXZD41frKQlyjACvTg90xVOU.png?width=1200)

コミット

全部ドラックアンドドロップ出来たら変化のコミットを押して完了

成功するとファイルがこんな感じでリポジトリのページに表示されます

![](https://assets.st-note.com/img/1738834355-UYCSwiFrEvGn5pI7WtLQKH34.png?width=1200)

コミット後

pen_app5リポジトリにファイルがダをアップロードできました。

次は、中央の右寄りのところにある設定を押します。

![](https://assets.st-note.com/img/1738834194-nLfhuEAY6mxoSdTX3kJzB8t4.png)

設定

そして、設定で開いた画面の左側のバーからページを選択します。

![](https://assets.st-note.com/img/1738834211-ioP5a8BbwvzmRuTQkYOg6jHF.png?width=1200)

ページ

そして、右側の2番目にセーブと書いてあるところがあるので、そこの先頭をメインにし、次は、ルートそして、セーブを押してます。(※メインにしてからセーブをおしましょう！)

セーブ

数分後同じページを開くとサイトのあるURLが公開されます。ここからアプリが表示されているページへ飛ぶことができます。

アプリ公開！

こんな感じで、アプリを公開することができます。

今回はこれで。

見ずらい記事ですみません。参考になれば幸いです。

ここまで読んでくださってありがとうございます！！

## いいなと思ったら応援しよう！