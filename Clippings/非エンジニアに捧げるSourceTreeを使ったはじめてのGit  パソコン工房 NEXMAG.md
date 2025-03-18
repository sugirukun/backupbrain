---
title: 非エンジニアに捧げるSourceTreeを使ったはじめてのGit | パソコン工房 NEXMAG
source: https://www.pc-koubou.jp/magazine/27266
author:
  - "[[パソコン工房 NEXMAG［ネクスマグ］]]"
published: 2019-11-11
created: 2025-03-18
description: Gitを簡単に利用できる「SourceTree」というツールを使って基本的な操作方法についてご説明したいと思います。SourceTreeは非エンジニアの方でも操作できるGitです。
tags:
  - git
---
![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_main.png)

![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_main-480x320.png)

[チャレンジ&ナレッジ](https://www.pc-koubou.jp/magazine/challenge)最終更新日:

複数人でソフトウェア開発などのプロジェクトを行う際に、「誰が」「いつ」「どのファイルに」「どのような」変更を加えたか、ソースコードのバージョン管理が必要となりますが、このような場合によく耳にするのが「Git（ギット）」です。 Gitは便利で強力なツールですが、コマンドラインで操作するイメージが強く、非エンジニアの方には敷居が高い印象を持たれている方も多いかと思います。 そこで今回は、Gitの基本的な操作方法について、Gitを簡単に使用することができる「SourceTree」というツールを使ってご説明したいと思います。

## Gitとは

GitはLinux OSを開発をしたことで知られるリーナス・トーバルズ氏が、「Linux」の中心となる部分の開発を、オープンソースで効率よく進めるために開発をしたバージョン管理システムです。

元々、OS の巨大なソースコードを管理するために作られたため、軽快に動作することに重点を置かれて開発されています。

先ほど出てきた「バージョン管理システム」とは特定のファイルの変更（新規作成、変更、削除）に対して、名前をつけて任意のタイミングで保存することができ、以前の変更地点まで巻き戻ることもできます。

他にも、複数人でのプロジェクトで自分以外の人とファイルを共有して、その人が変更した箇所の確認を行うことや、変更された内容を自分のファイルに取り込むことも可能です。

## SourceTreeをインストール

便利なGitですが、実際に使用するには「コマンドプロンプト」内でコマンドを打ってGit を操作する必要があり、初心者にとってはハードルの一つとなっています。

そこで今回は「SourceTree」というGUIツールを用います。

※GUI（Graphical User Interface）ツール・・・通常のアプリケーションソフトと同じようにコマンドラインではなく視覚的な操作により使用するツール。一方、コマンドラインで操作するツールのことをCLI（Command Line Interface）ツールという。

SourceTreeは、ウインドウ操作でGitを簡単に操作することのできるGUIツール（Gitクライアントとも呼ばれます）です。

Gitをコマンドで実行して操作する場合、複数人などのプロジェクトで、今誰がどのファイルを編集しているのか、直感的に把握することが難しくなります。

その点SourceTreeはGUIツールなので、操作のしやすさに加えて、直感的にファイルがどういう状態で管理されているのかがわかりやすくなっています。

他のGitクライアントでは、別途Gitをインストールして使う環境を設定しなければいけないものもありますが、SourceTreeをインストールすると、Git本体も同時にインストールされ、すぐにGitが使えるようになる点も魅力です。

それでは、実際にSourceTreeを使ってみましょう。

まずは下記のサイトからダウンロードして、インストールします。

“Sourcetree | Free Git GUI for Mac and Windows”．Atlassian．2019．  
[https://www.sourcetreeapp.com/](https://www.sourcetreeapp.com/)

[![公式サイトからダウンロードを開始します](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image02.png "公式サイトからダウンロードを開始します")](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image02.png)公式サイトからダウンロードを開始します

サイトからダウンロードが完了したら、ダウンロードしたファイルを実行します。

実行後、下図のような画面が表示され画面の指示に従いインストールを進めますが、まずは下図の赤枠部分のリンクをクリックして、アカウントを作成する必要があります。

[![アカウントを持っていない場合は上図赤枠のリンクからアカウントを新規作成する](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image03.png "アカウントを持っていない場合は上図赤枠のリンクからアカウントを新規作成する")](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image03.png)アカウントを持っていない場合は上図赤枠のリンクからアカウントを新規作成する

リンクをクリックすると下記の画面が表示されるので、設定したいユーザー名を入力して「続行」ボタンをクリックします。

[![希望のユーザー名を入力して「続行」ボタンをクリックする](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image04.png "希望のユーザー名を入力して「続行」ボタンをクリックする")](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image04.png)希望のユーザー名を入力して「続行」ボタンをクリックする

無事にアカウント登録ができると、下図のような画面が表示されアカウント登録が完了します。

下図赤枠の「次へ」をクリックします。

[![「アカウント登録完了」画面](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image05.png "「アカウント登録完了」画面")](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image05.png)「アカウント登録完了」画面

次の画面では、「Git」のチェックボックスをオンにして「次へ」をクリックします。

[![「Git」にチェックすることでGitもインストールする](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image06.png "「Git」にチェックすることでGitもインストールする")](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image06.png)「Git」にチェックすることでGitもインストールする

Gitのインストールが開始されます。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image07.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image07.png)

ツールのインストールが完了しました。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image08.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image08.png)

次の画面でログイン情報を設定します。

先ほど登録したユーザー名とメールアドレスが入っていることを確認して「次へ」をクリックします。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image09.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image09.png)

次の画面では「SSHキーを読み込みますか？」と聞かれますが、ここでは「いいえ」を選択します。

[![ここでは「いいえ」をクリック](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image10.png "ここでは「いいえ」をクリック")](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image10.png)ここでは「いいえ」をクリック

設定が完了すると、SourceTreeが起動します。

[![起動したSourceTreeの画面](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image11.png "起動したSourceTreeの画面")](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image11.png)起動したSourceTreeの画面

これでSourceTreeを使用する設定が終わりました。

## SourceTreeを使ってGitの基本的な操作をする（ローカルでの操作）

SourceTreeを使うには、Gitの基本的な操作について知っておく必要があります。

ここからは、実際にSourceTreeを使いながら、基本的な操作について説明します。

### リポジトリを作る

リポジトリとは、ファイルの変更点を記録しておくフォルダのことを指します。これからバージョン管理を行っていく上でとても重要な保存場所とも言えます。

実際にリポジトリを作ってみます。デスクトップに新しいフォルダを作成しますが、フォルダ名は特に指定はないので好きな名前で作成します。

今回は「file」という名前でフォルダを作成しました。

新しいフォルダができたら、SourceTreeに戻り、下図赤枠の「Create」をクリックします。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image13.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image13.png)

続いて、「参照」をクリックして先ほど作成したフォルダを指定します。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image12.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image12.png)

これでリポジトリを作成することができました。

### コミットをする

コミットとは、ファイルの変更点に名前をつけて記録することを指します。

こちらもGitを使う上で重要な操作です。

まずWindowsのファイルエクスプローラーで先ほど作成した「file」フォルダに「text.txt」を新規作成します。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image14.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image14.png)

ファイルを作成した後でSourceTreeの画面を確認すると、左メニューにある「ファイルステータス」の「作業ツリーのファイル」に「text.txt」が表示されます。

SourceTreeの「作業ツリーのファイル」は、リポジトリを作成したフォルダ内で監視を行なっており、フォルダの内容が変更がされた場合、そのファイル名と変更内容が表示される仕組みになっています。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image15.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image15.png)

「作業ツリーのファイル」に「text.txt」が表示されたことが確認できたら、「text.txt」の隣の「＋」ボタン（上図赤枠）をクリックします。

もしくは、「全てのインデックスに追加」ボタン（上図青枠）をクリックします。

すると、上の枠内「indexにステージしたファイル」に「text.txt」が移動しました。

この操作はステージングと呼ばれ、どのファイルの変更点を記録するか選ぶことを指します。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image16.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image16.png)

なお、ステージングをキャンセルしたい場合は、「indexにステージしたファイル名の横にある「-」ボタン（下図赤枠）をクリックすると、ステージングをキャンセルすることができます。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image17.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image17.png)

ステージングをして、どのファイルの変更点を記録するか選択できたら、いよいよコミットします。

「コミット」ボタンの上にあるテキスト入力欄に、「どのような変更を行った」のか入力する必要があります。

今回はファイルを追加しただけなので、「テキストファイルの追加」と記入して、「コミット」ボタンをクリックします。

※ソースコードの場合は、「～機能を変更・追加・修正」のように入力することが多いです

[![変更内容を入力して「コミット」ボタンをクリック](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image18.png "変更内容を入力して「コミット」ボタンをクリック")](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image18.png)変更内容を入力して「コミット」ボタンをクリック

コミットボタンをクリックした後、左メニューの「History」をクリックすると、下図のように「テキストファイルの追加」が変更（コミット）履歴として記録されているのが確認できます。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image19.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image19.png)

### テキストファイルを変更して、コミットする

続いて「file」フォルダ内の「text.txt」をメモ帳などのテキストエディタで開き、「テスト」と書いて上書き保存します。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image20.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image20.png)

上書き保存ができたらSourceTreeに戻り、左メニュー「ファイルステータス」の「作業ツリーファイル」に、「text.txt」が表示されていることを確認してください。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image21.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image21.png)

先ほど同様に、「text.txt」の「＋」ボタンをクリックするまたは、「全てのインデックスに追加」ボタンを押してステージングします。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image22.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image22.png)

「コミット」ボタンの上にあるテキスト入力欄に、「テキストの追加」と入力して、「コミット」ボタンをクリックします。

先ほどと同様、左メニューに「History」をクリックすると、「テキストの追加」が変更（コミット）履歴として記録されていることが確認できます。

[![「テキストの追加」が履歴として追加された](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image23.png "「テキストの追加」が履歴として追加された")](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image23.png)「テキストの追加」が履歴として追加された

### コミットの取り消し

Gitでは、コミットして変更したファイルを以前の状態に戻したい時、任意の変更点に戻すことができます。これを「コミットの取り消し」といいます。

コミットの取り消しには、「reset」「revert」の2種類があり、「reset」は、最新コミットから任意のコミットまでを削除しますが、もとに戻すことが不可能になります。

もう一つの「revert」は、最新コミットから任意のコミットまでの変更点を削除する新たなコミットを作り出します。

「reset」は、コミットを取り消して記録を残したくないときに使用し、「revert」はコミットを取り消した記録を残しておきたいときに使用します。

今回は「reset」でのコミットの取り消しを実行します。

まず、SourceTree上の左メニュー内の「History」で「ファイルの追加」を右クリックして、「現在のブランチをこのコミットまでリセット」を選択します。

[![変更点「ファイルの追加」を右クリックし「現在のブランチをこのコミットまでリセット」をクリック](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image24.png "変更点「ファイルの追加」を右クリックし「現在のブランチをこのコミットまでリセット」をクリック")](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image24.png)変更点「ファイルの追加」を右クリックし「現在のブランチをこのコミットまでリセット」をクリック

クリックすると、下図のようなモーダルウインドウが開くので使うモードを「Hard- 全ての作業コピーの変更を破棄する」を選択して、「OK」をクリックします。

[![「Hard- 全ての作業コピーの変更を破棄する」を選択して、「OK」をクリック](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image25.png "「Hard- 全ての作業コピーの変更を破棄する」を選択して、「OK」をクリック")](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image25.png)「Hard- 全ての作業コピーの変更を破棄する」を選択して、「OK」をクリック

「OK」をクリックすると、実行されて変更履歴が、「テキストファイルの追加」だけになり、先ほどまで存在していた「テキストの追加」が削除されています。

実際に「file」フォルダの「text.txt」を開くと、「テキストファイルの追加」の時点、「テスト」入力前まで戻されていることが確認できます。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image26.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image26.png)

[![「text.txt」の内容が「テスト」入力前まで戻されている](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image27.png "「text.txt」の内容が「テスト」入力前まで戻されている")](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image27.png)「text.txt」の内容が「テスト」入力前まで戻されている

### コミットする前に変更点を取り消す

ステージングしてコミットする前に、以前変更した部分を取り消すこともできます。

まず「file」フォルダ内の「text.txt」に、「テスト」と書いて上書き保存します。

SourceTreeの左メニュー「ファイルステータス」の「作業ツリーのファイル」に、「text.txt」が表示されるので、「作業ツリーのファイル」上の「text.txt」を右クリックして、「破棄」を選択します。

[![「text.txt」を右クリックして「破棄」をクリック](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image28.png "「text.txt」を右クリックして「破棄」をクリック")](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image28.png)「text.txt」を右クリックして「破棄」をクリック

「破棄」をクリックしたら、「file」フォルダ内の、「text.txt」を開いて確認すると、先ほど上書き保存した「テスト」の文字が消えています。

### ブランチを切る

Gitでは複数のファイル変更を行って見比べるときに、変更点を分岐することができ、これを「ブランチ」と呼びます。ブランチには「枝」という意味があり、変更点を枝分かれさせることを「ブランチを切る」と言います。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image29.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image29.png)

左メニュー「History」をクリック後、「テキストファイルの追加」を右クリックして、「ブランチ」を選択します。

[![「キストファイルの追加」を右クリックして「ブランチ」を選択](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image30.png "「テキストファイルの追加」を右クリックして「ブランチ」を選択")](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image30.png)「テキストファイルの追加」を右クリックして「ブランチ」を選択

下図のようなモーダルウィンドウが表示されるので、「新規ブランチ」の隣に「test1」と入力して、「ブランチを作成」をクリックします。

[![新規ブランチの欄に「test1」と入力して「ブランチを作成」ボタンをクリック](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image31.png "新規ブランチの欄に「test1」と入力して「ブランチを作成」ボタンをクリック")](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image31.png)新規ブランチの欄に「test1」と入力して「ブランチを作成」ボタンをクリック

再度上記と同じ手順で、新規ブランチ「test2」も作ります。

[![同様に「test2」ブランチも作成する](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image32.png "同様に「test2」ブランチも作成する")](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image32.png)同様に「test2」ブランチも作成する

左メニュー「ブランチ」の下に「master」の他に、「test1」と「test2」が追加されていることを確認します。

これは、ブランチ「master」から、ブランチ「test1」、ブランチ「test2」という「枝」が作られたことを意味します。

[![「master」から「test1」「test2」のブランチが作られた状態](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image33.png "「master」から「test1」「test2」のブランチが作られた状態")](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image33.png)「master」から「test1」「test2」のブランチが作られた状態

上図「test2」の左についている「◯」が現在選択しているブランチを表しています。隣の「test1」をクリックしてみると「test1」が「◯」の隣に移動します。選択中のブランチを変更することを「チェックアウト」と呼びます。

[![クリックした「test1」を選択すると「○」の側に移動した](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image34.png "クリックした「test1」を選択すると「○」の側に移動した")](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image34.png)クリックした「test1」を選択すると「○」の側に移動した

「file」フォルダ内の「text.txt」に「テスト1」と書いて上書き保存します

[![「text.txt」に「テスト1」と書いて上書き保存](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image35.png "「text.txt」に「テスト1」と書いて上書き保存")](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image35.png)「text.txt」に「テスト1」と書いて上書き保存

この変更を「テスト1の追加」として、ステージングさせてコミットします。

[![「テスト1の追加」としてコミット](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image36.png "「テスト1の追加」としてコミット")](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image36.png)「テスト1の追加」としてコミット

左メニュー内の「ブランチ」の下の項目にある「test2」をクリックして、ブランチ「test2」にチェックアウトします。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image37.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image37.png)

先ほどの変更は、ブランチ「test1」に対して行われたので、「file」フォルダ内の「test.txt」を開いても

先ほど変更した「テスト1」は書かれていません。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image38.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image38.png)

では、次に「test.txt」に「テスト2」と書いて上書き保存します。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image39.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image39.png)

この変更を「テスト2の追加」として、ステージングしてコミットします。

[![「テキスト2の追加」](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image40.png "「テキスト2の追加」")](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image40.png)「テキスト2の追加」

左メニュー「History」を見るとブランチ「master」から、2つのコミットが枝分かれしていることが確認できます。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image41.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image41.png)

### スタッシュを使う

選択中のブランチは、左メニュー「ブランチ」のブランチ名をクリックすることで変更（チェックアウト）することができますが、現在のブランチでコミットされていない変更点がある場合は、ブランチを切り替えることができません。

その場合に、変更点を一時的にスタッシュに記録させておくことができます。

ブランチ「test2」を選択した状態で、「file」フォルダ内の「text.txt」に下図のようにテスト2,テスト3と書いて、上書き保存します。（テスト2の下にテスト3を追加する形になっていることを確認してください。）

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image42.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image42.png)

この状態で、ブランチ「test1」に変更しようとすると、コミットされていない変更点があるため、エラーが発生してチェックアウトすることができません。

[![「コミットされていない変更があります」と表示される](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image43.png "「コミットされていない変更があります」と表示される")](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image43.png)「コミットされていない変更があります」と表示される

そこで、スタッシュをします。  
下図赤枠の「スタッシュ」をクリックして、スタッシュ名を「テスト3」として「OK」ボタンをクリックします。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image44.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image44.png)

「OK」をクリックすると、左メニュー「スタッシュ」に「0:On test2: テスト3」として、ブランチ「test2」の変更が「テスト3」として保存されていることを確認します

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image45.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image45.png)

この状態で、左メニュー「ブランチ」の下の「test1」をクリックして、ブランチ「test1」に変更（チェックアウト）します。  
今度はエラーが発生しません。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image46.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image46.png)

再度ブランチ「test2」に切り替えます。

スタッシュに退避した変更点を戻す場合は、左メニュー「スタッシュ」の「0:On test2: テスト3」を右クリックして、「スタッシュ ‘0:On test2: テスト3’を適用」をクリックします。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image47.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image47.png)

スタッシュを削除する場合は、左メニュー「スタッシュ」の「0:On test2: テスト3」を右クリックして、「スタッシュ ‘0:On test2: テスト3’を削除」をクリックすると削除できます。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image48.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image48.png)

「テスト3」として変更した点は、「テスト3の追加」と記載してコミットしておきます。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image49.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image49.png)

### マージをする

Gitの操作において「マージ」も頻繁に使う操作の一つです。

「マージ」とは複数のブランチの変更点を、一つのブランチに統合し、まとめる操作のことを指します。

先ほど切ったブランチをマージしてみます。  
ブランチ「master」にチェックアウトします。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image50.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image50.png)

「file」フォルダ内の「test.txt」に何も書かれていないことを確認します。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image51.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image51.png)

左メニュー「ブランチ」の下の「test2」を右クリックして、「現在のブランチにmasterをマージ」を選択します。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image52.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image52.png)

上記の操作により、ブランチ「test2」の内容が、ブランチ「master」に適用され、「text.txt」に下図のように  
テスト2  
テスト3  
と書かれました。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image53.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image53.png)

簡単にマージをすることができましたが、マージする際の注意点として、コンフリクト（衝突）があります。

コンフリクトとは、同じファイルの同じ箇所を変更した場合、ブランチを結合しようとすると、Gitがどちらを採用していいのかわからなくなり、発生してしまうものです。

コンフリクトが発生した場合は、解消して、コミットする必要があります。

ブランチ「test1」にチェックアウトします

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image54.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image54.png)

左メニュー「ブランチ」の下の「test2」を右クリックして、「現在のブランチにtest2をマージ」を選択します。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image55.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image55.png)

コンフリクトが発生するので、左メニュー「ファイルステータス」をクリックし、コンフリクトが発生している「test.txt」を選択します。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image56.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image56.png)

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image57.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image57.png)

コンフリクトしたファイルの中身を確認すると、下図のようになっています。

コンフリクトが発生すると、下記の表記で表されます。

```
コンフリクトは、下記の表記で表される
<<<<<<<<<<<HEAD
現在のブランチの変更内容（自分）
===============
マージするブランチの変更内容（相手）
>>>>>>>>>>>
```

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image58.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image58.png)

コンフリクトが起きた場合、「test.txt」を右クリックして、「競合を解決」の中から、現在のブランチの変更内容を採用したい場合は「’自分の変更’を使って解決」を、マージするブランチの変更内容を採用したい場合は「’相手の変更’を使って解決」を選択します。

[![](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image01.png)](https://www.pc-koubou.jp/magazine/wp-content/uploads/2019/09/git_beginner_image01.png)

コンフリクトを解消したい場合のその他の選択肢として、「test.txt」を開いて、内容を修正する対策もありますが、コンフリクトが解消したら、「コミット」ボタンを押してコミットすることは忘れないでください。

## Gitは初心者でも使える

今回は、Gitで主に使う操作方法をGUIツールのSourceTreeを用いて説明しました。Gitは今ではエンジニアだけではなく、デザイナーや他の職種でも使われる頻度が高く、プロジェクトを管理する上でも必要なものになってきています。

CUIでの操作が苦手な人もSourceTreeを使うと比較的わかりやすくGitを操作することができるので、ぜひこの機会に挑戦していただければと思います。

いいネ！と思ったらクリック！[28](https://www.pc-koubou.jp/magazine/# "Like this")

[パソコン工房セール特集](https://www.pc-koubou.jp/pc/sale_portal.php?pre=nexmag_toiawase&utm_source=nexmag&utm_medium=content&utm_campaign=content_bottom_banner&utm_content=nonpay)

この記事をシェアする