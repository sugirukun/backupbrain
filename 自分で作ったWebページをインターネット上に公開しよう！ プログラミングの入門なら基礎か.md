---
tags:
  - github
---



作成日: 2025/02/26
URL: https://prog-8.com/docs/github-pages

# **自分で作ったWebページをインターネット上に公開しよう！**

この記事では、**自分のPC等で作成したWebページを、インターネット上に公開する方法**を学習します。Webページを公開するには様々な方法がありますが、今回は「**GitHub**」というサービスを用いて無料で公開してみましょう。

**◯ 必要な知識**・HTMLおよびCSSの基礎的な知識Progate「[HTML & CSS 学習コース 初級編](https://prog-8.com/lessons/html/study/1)」をクリアしていれば十分です。

※ 今回は「GitHub」というWebサービスを利用しますが、「git」の知識は不要です。※ 記事内で使用している画像は全て「Mac」で撮影したものですが、「Windows」でも同じように進めることができるのでご安心ください。

# **1. Webページを公開する流れ**

実際に作業を開始する前に、「GitHub」でWebページを公開するまでの流れを簡単に確認してみましょう。

まずは自分のPCで公開したいWebページを作成してみましょう。この方法に関しては「[HTML & CSS の開発環境を用意しよう！](https://prog-8.com/docs/html-env)」という記事で紹介していますので、わからない人はこちらを参考にしてみてください。※ 今回はこちらでサンプルコードを用意してありますので、自分でWebページを用意していなくても学習を進めることは可能です。

Webページを用意したら、その際に作成したHTMLファイルやCSSファイル、さらには画像などを「GitHub」上にアップロードしていきます。「GitHub」のアカウントを持っていない場合には、その前に無料登録をする必要があります。

最後に、アップロードしたファイルに「GitHub」上で設定を加えることで、無料でWebページを公開することができます。

「Webページを公開する」というと、難しい作業が続くようなイメージを持つ方もいるかもしれません。ですが、これらのそれぞれ作業は非常にシンプルなものですので安心してください。

では次の章から実際に作業を開始していきましょう！

# **2. GitHubのアカウント作成**

まずは「GitHub」の無料アカウントを作成しましょう。以下のURLにアクセスしてください。

[https://github.com/](https://github.com/)

**※ すでにGitHubのアカウントを持っている場合**上記URLからGitHubにログインができましたら、この章は飛ばして次の「リポジトリの作成」へ進んでください。

以下の画像のようなページにアクセスできましたか？

![](https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/3/1522317856801.png)

*「github.com」のトップページ*

画面右側に表示されている入力フォームに、「ユーザー名」「メールアドレス」「パスワード」をそれぞれ入力して、緑色の「Sign up for GitHub」というボタンをクリックしてください。なお、ここで入力した「ユーザー名」は後ほど公開するWebページのURLの一部になります。

ユーザー名やパスワード等に問題がなければ以下のような利用プランの画面が表示されたかと思います。

![](https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/34/1561022753682.png)

今回は無料アカウントで十分ですので、画像のように「Unlimited public repositories for free.」にチェックが入っていることを確認してから緑の「Continue」ボタンをクリックしてください。

その後、アンケートを入力する画面が表示されますが、ここは特に何も入力せずに一番下の緑のボタンをクリックすれば大丈夫です。

以下のような画面のページが表示できたでしょうか？これでGitHubのアカウントが作成できました。

![](https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/3/1522317902777.png)

*この画面が表示されればOKです*

これから先の作業を続けるには、GitHubに登録したメールアドレスを認証する必要があります。GitHubからメールが届いているはずですので、確認してください。

# **3. リポジトリの作成**

次は「リポジトリ」というものを作成していきます。リポジトリとは、1つのWebページやアプリケーションなどをGitHub上で管理するためのプロジェクトのようなものです。

以下の画像を参考に、画面右上のプラスアイコン「+」をクリックし、「New repository」を選択してください。

![](https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/3/1522321194344.png)

表示されたページの中央にある、「Repository name」という入力欄にリポジトリ名を入力します。リポジトリ名は基本的に何でも大丈夫ですが、ここで設定したリポジトリ名によって、この後公開するWebページのURLが変わってきます（以下参照）。

**「アカウント名.github.io」とした場合**公開URLは `https://アカウント名.github.io` となります。

**上記以外の場合**公開URLは `https://アカウント名.github.io/リポジトリ名` となります。

つまり、ユーザー名を `prog-8` とした場合、リポジトリ名を `prog-8.github.io` とすれば `prog-8.github.io` というURLに、リポジトリ名を `sample` とすれば `prog-8.github.io/sample` というURLになります。

今回は特に理由がなければ上の「アカウント名.github.io」で作ってみましょう（リポジトリ名はあとから変更可能です）。

![](https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/3/1522321217149.png)

リポジトリ名を入力したら、緑色の「Create repository」ボタンをクリックしてください。

これでリポジトリを作成することができました。表示された画面にて、以下の画像を参考に「README」というリンクをクリックしてください。

![](https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/3/1522321237367.png)

[[]]」（リードミー）とは、このリポジトリの説明を書くためのファイルです。今回は特に何も書く必要はないので、何もせずに右の緑の「Commit changes...」というボタンを押してください。

では次の章で、HTMLやCSSのファイルをアップロードする方法を学んでいきましょう！

# **4. ファイルのアップロード**

**◯ HTML・CSSファイルのアップロード**

まずは「**index.html**」というHTMLファイルを用意していきましょう。

「Create new file」メニューを選択しファイルの追加画面を開きましょう。

![](https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/3/161225912483.png)

*ファイルの追加*

つぎに、以下の画像を参考に、入力欄にファイル名である「**index.html**」を入力しましょう。自分でWebページを作成した人は、ファイル名が「index.html」ではない場合もあるかと思いますが、ここは必ず「index.html」にしてください。

![](https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/3/1522321275979.png)

*ファイル名「index.html」を入力*

その下の「Edit new file」の欄には、自分が書いたHTMLのコードをまるごとコピーして貼り付けてください。

![](https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/3/15223213254.png)

*HTMLのコードを全てコピーして貼り付け*

まだ自分でWebページを制作していない、という人は、今回は練習として[こちら](https://raw.githubusercontent.com/prog-8/prog-8.github.io/master/index.html)にあるコードをコピーして利用してください。

ここまでできたら、一番下の緑のボタンを押しましょう。これでGitHub上にHTMLファイルを用意することができました。

次は、CSSファイルをアップロードします。手順はHTMLのときと同じです。今回はファイル名は「index.html」のコード内で指定しているファイル名にしましょう（以下の画像の例では「stylesheet.css」としてあります）。

![](https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/3/1522321327676.png)

*「stylesheet.css」を追加*

サンプルコードが必要な方は[こちら](https://raw.githubusercontent.com/prog-8/prog-8.github.io/master/stylesheet.css)をご利用ください。

**◯ 画像のアップロード**

コードがアップロードできたので、次は画像ファイルをアップロードする方法を見てみましょう。

先ほどクリックした「Create new file」というボタンの下にある「

**Upload files**

」というボタンをクリックしてください。

![](https://prog-8.com/shared/images/document/3/1655710001471.png)

表示された画面の真ん中に、HTMLやCSS内で使っている画像をドラッグアンドドロップしましょう。「choose your files」というリンクを押すことでもアップロード可能です。

![](https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/3/1522322675440.gif)

アップロードしたい画像がない場合には、練習として[こちら](https://raw.githubusercontent.com/prog-8/prog-8.github.io/master/top.png)のサンプル画像をダウンロードしてGitHubにアップロードしてみましょう。

アップロードできたら、緑色の「Commit changes」というボタンを押すことで保存が完了します。

アップロードしたファイルは以下の画面から確認することができます。

![](https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/3/1522321442474.png)

各ファイル名の部分をクリックすることでそのファイルの中身も確認できますので、正しくアップロードできているか確認してみましょう。

# **5. ページの公開**

**注**：2020年10月1日から、GitHubで作成された新しいリポジトリの**デフォルトブランチ**の名前は、**master**から**main**に変更されました。変更の詳細については、[こちら](https://github.com/github/renaming)をご覧ください。

それではアップロードしたファイルを用いて、Webページを公開してみましょう。まず、画面右上の「**Settings**」というリンクをクリックしてください。

![](https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/3/1522393938441.png)

Settingページの左側にあるメニューの中から「Pages」をクリックしてください。

![](https://prog-8.com/shared/images/document/3/166130927363.png)

上の画像のように、「Your site is live at ...」と表示されている場合には、そこに表示されているURLですでにWebページが公開されています。

もし表示されていない場合には、「Branch」の項目が「**None**」となっていると思いますので、これを**デフォルトブランチ**（リポジトリが作成された時期に応じて、「**master**」または「**main**」）に変更して「Save」ボタンを押すことでURLが表示されます。

これで自分のWebページをインターネット上に公開するための作業は終了です。これで自分が作ったページに、自分だけでなく友達などの他の人でもそのURLからアクセスすることができます！

※ もしURLにアクセスしても何も表示されない場合には、ページを表示する処理に時間がかかっている可能性があります。少し待ってから再度ページを読み込んでみてください。

# **6. 公開したページの更新**

最後に、公開したWebページを更新する方法を学習しましょう。今回使用している「 GitHub Pages」では、GitHubにアップロードしているファイルのコード更新するだけで、自動で数分後に公開してあるWebページも更新してくれます。

今回は試しに「index.html」を更新してみます。画面左上の「**Code**」の部分をクリックし、表示されたページ内の「**index.html**」をクリックします。

![](https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/3/1522321875276.png)

ファイルの中身が確認できたかと思います。その画面で、右上に表示されている鉛筆マークをクリックします。

![](https://s3-ap-northeast-1.amazonaws.com/progate/shared/images/document/3/15223218778.png)

表示された画面で「index.html」のコードを編集することが可能です。編集が終わったら、一番下の緑色の「Commit changes」というボタンを押して保存しましょう。

また、ファイルの削除は先ほどの鉛筆マークの右側にあるゴミ箱マークをクリックすることで可能です。

GitHubを用いてWebページを公開する方法はこれで以上です。もし、お気に入りのオリジナルWebページを作成して公開できたら、是非Twitterやご意見箱からご報告ください！Progate一同、皆さんから嬉しい報告が届くのを楽しみにしています！