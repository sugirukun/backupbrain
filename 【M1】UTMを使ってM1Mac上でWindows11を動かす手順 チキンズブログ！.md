# 【M1】UTMを使ってM1Mac上でWindows11を動かす手順 | チキンズブログ！

[https://www.chickensblog.com/m1mac-win11/](https://www.chickensblog.com/m1mac-win11/)

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-81.png)

M1Mac

## ※注意

この記事は、[Zennで書いた記事の一部](https://zenn.dev/teba_eleven/articles/aedc265d30e751)です。

まだ読んでいない方は先にこちらの記事をお読みください。

![](https://www.chickensblog.com/wp-content/uploads/cocoon-resources/blog-card-cache/1cf05a834608766051d2fa22b5c076e6.png)

[【革命！】M1MacでWindows11を無料&快適に動かす...zenn.dev](https://zenn.dev/teba_eleven/articles/aedc265d30e751)

## homebrewのインストール

[](https://s.wordpress.com/mshots/v1/https%3A%2F%2Fbrew.sh%2Findex_ja?w=320&h=180)

[Page not found · GitHub...brew.sh](https://brew.sh/index_ja)

iterm2やターミナルでhomebrewをインストールします。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-11.png)

ターミナルにコマンドを貼り付けてEnterで実行してください。

細かいインストール方法は[こちらの記事](https://zenn.dev/kawacdev/articles/510ea6c75ae793)が参考になると思います。

## UTMのインストール

```
$ brew install --cask utm
```

GUIアプリを入れるので--caskオプションをつけておきます。

## Windows11のダウンロード

[UUP dump](https://uupdump.net/)というサイトからダウンロードしていきます。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-12.png)

今回はLatest Beta Channel buildのarm64を選択します。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-13.png)

![](https://www.chickensblog.com/wp-content/uploads/cocoon-resources/blog-card-cache/7a7f45f3bf4950976434d06f2ece458f.png)

[Select language for Windows 11...Select language for Windows 11 Insi...uupdump.net](https://uupdump.net/selectlang.php?id=152f1d3b-dc4c-4e6e-a139-cc3039968402)

現在は三つほどのバージョンがありますが、筆者は真ん中を選択しました。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-14.png)

言語は日本語にして次へ。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-15.png)

いじらず次へ。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-16.png)

- Conversion optionsの一番上のチェックを外す

画像と同じ状態にしたらCreate download packageボタンを押す。

これでzipがダウンロードされるので、解凍されてできたフォルダはデスクトップなどのわかりやすい場所に置いておきましょう。自分はデスクトップに置きました。

## homebrewを使ったISOファイルの準備

### Windows11インストールファイルの作成

```
$ cd (さっき解凍したフォルダ)
```

ターミナルでさっき解凍したフォルダのパスに移動

```
$ bash uup_download_macos.sh

One of required applications is not installed.
The following applications need to be installed to use this script:
 - aria2c
 - cabextract
 - wimlib-imagex
 - chntpw
 - genisoimage or mkisofs
```

これでインストールすべきものが出てくるので、homebrewを使って入れていきます。

```
$ brew tap sidneys/homebrew
$ brew install aria2 cabextract wimlib cdrtools sidneys/homebrew/chntpw
```

```
$ bash uup_download_macos.sh
```

isoファイルをダウンロードするスクリプトを実行

```
$ ls
22621.1_MULTI_ARM64_JA-JP.ISO files （バージョンにより名前が違う）
ConvertConfig.ini             uup_download_linux.sh
UUPs                          uup_download_macos.sh
aria2_download.log            uup_download_windows.cmd
aria2_script.26595.txt
```

- 22621.1_MULTI_ARM64_JA-JP.ISO（バージョンにより名前が違う）

ファイルは、自分の好きな場所に置いておく。

自分はデスクトップに「windows」というフォルダを作り、

- windowsフォルダ
    - 22621.1_MULTI_ARM64_JA-JP.ISO （バージョンにより名前が違う）

こんな感じにファイルを管理しています。

## UTMを使ったWindows11の仮想環境作成

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-17.png)

画像には左側にWindows11と表示されていますが、ないものと思ってください。

（先に筆者が作った環境が表示されています）

homebrewでインストールしたUTMはアップフォルダに入っているので起動し、

- Create a new Virtual Machine

をクリック

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-18.png)

- Visualize

を選択

### OS選択

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-19.png)

- Windows

を選択

### ネット接続に必要なファイルのダウンロード

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-20.png)

一番下にある青文字の、

- SPICE tools and QEMU dtrivers

をクリック

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-22.png)

Downloadsの下にある青文字の

- Download

をクリック

- spice-guest-tools-0.164.3.iso(バージョンによって名前が違う)

がダウンロードされます。このファイルも好きな場所に配置してください。

自分はデスクトップに「windows」というフォルダを作り、

- windowsフォルダ
    - 22621.1_MULTI_ARM64_JA-JP.ISO （バージョンにより名前が違う）
    - spice-guest-tools-0.164.3.iso (バージョンによって名前が違う)

こんな感じに管理しています。

### 起動用ファイルの選択

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-23.png)

一番上にあるチェック、

- import VHDX Image

のチェックをはずしておきます。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-25.png)

- Browse...

とかかれたボタンをクリックし、一番最初にインストールした

- 22621.1_MULTI_ARM64_JA-JP.ISO (バージョンによって名前が違う)

を選択します。

それができたら下のContinueを押して先に行きます。

### メモリの設定

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-26.png)

メモリサイズは

- 6144MB（6GB）

にしておきます。

4GBや、8GBの8192MBでも良いのですが、4GBだと少なすぎるし、8GBだと自分のMacのメモリだと厳しそうなので中間の6GBにしました。

お使いの環境によって変えてください。（少なすぎるとダメです）

### 共有ストレージサイズの設定

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-27.png)

仮想で動かしているWindowsとMac本体の共有のフォルダサイズになります。SSDに余裕がある方は128GBなどにした方が良いと思います。

自分はMacの容量がないのでデフォルトの64GBのままでいきました。

容量は基本固定されるので、多めにとっておいた方が良さそうです。

※変更する方法もあると思いますが、筆者はまだ見つけれられていません。

### 共有ストレージディレクトリの設定

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-28.png)

シェアするディレクトリの位置を聞かれるので、

- Browse...

ボタンを押してお好みのフォルダやディレクトリに設定してください。

自分は

- ShareFile

のようなフォルダをデスクトップ上に作成して、それを選択しました。

### 環境名の設定

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-29.png)

仮想マシンの情報が表示されます。一番上にある

- Name

には自分が判断できる仮想マシンの名前を入れておきましょう。今回はWindows11なので、Windows11とだけ入れておけば良いと思います。

※同じWindows11の環境を複数作る場合は名前を変えないとわかりにくくなります

### 環境の作成確認

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-30.png)

こんな感じに左側に環境が追加されたらおkです。

画像には一番上に

- Windows11

という環境が既にありますが、先にテストして追加されたものなので、気にしないでください。

## 起動&解像度の変更

それでは実際に起動します。三角のボタンを押すと起動します。

### 解像度の設定

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-32.png)

画面が立ち上がった瞬間に、Escapeボタンを押します。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-33.png)

このような画面が出てきたら成功です。もし失敗してしまったら、ウィンドウをバツボタンで消して再度チャレンジしてみてください。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-34.png)

矢印キーで黒いカーソルを

- Device Manager

まで持っていき、Enter。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-35.png)

そして下に行き、

- DVMF Platform Configuration

を選択してEnter。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-36.png)

- Change Preferred

の右にある数値にカーソルを持っていき、Enter。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-37.png)

- 1024×768

を選択してEnter。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-38.png)

F10を押した後にYを押して変更を保存します。

Escapeを2回押してトップ画面に戻り、Continueを選択しEnter。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-92.png)

このような画面が出てきたら、スペースキーなどのキーを押します。

### インストールするためにレジストリを設定

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-39.png)

スペースキーを押した後、お馴染みのWindowsのインストーラー画面が出てきました。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-44.png)

このままインストールしたいのですが、設定をしないとできません。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-40.png)

ShiftとF10を同時に押すとターミナルが出てきます。

```
regedit
```

と入力しEnter。

文字が打てない時はマウスを一度ターミナル内でクリックしましょう

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-41.png)

レジスタエディタが開きました。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-42.png)

- HKEY_LOCAL_MACHINE
    - SYSTE
        - Setup

を見つけ出します。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-43.png)

Setupの上で右クリックをして

- 新規
    - キー

を選択します。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-45.png)

名前は

- LabConfig

にします。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-49.png)

同じように右側の空白部分で右クリックし、

- キー
    - DWORD（32Bビット） 値（D）

を選択。

名前は

- BypassTPMCheck

にします。

同じ手順で

- BypassSecureBootCheck

を作成します。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-50.png)

BypassTPMCheckをダブルクリックし、値を1に設定します。設定できたらOKを押す。

同じようにBypassSecureBootCheckの値も1に設定し、OKを押します。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-51.png)

こんな感じに、一番右側の（）内が1になっていれば大丈夫です。0だった場合は再度設定しましょう。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-52.png)

レジストリエディタを右上のバツボタンで消し、ターミナルに

```
exit
```

と打ち込みEnter。

文字が打てない時はマウスを一度ターミナル内でクリックしましょう

### Windows11のインストール

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-53.png)

これで最初の画面に戻れたので、今すぐインストールを押していきます。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-54.png)

プロダクトキーがありませんを選択

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-55.png)

自分はProの方が良さそうだったのでそっちを選びましたが、お好みで。次へを押します。

レジストリをいじったおかげでこの画面を表示できました。

同意して次へ。

下のカスタムを選択。

次へ。

インストールが始まるので待ちます。

インストーラーが終わると再起動が勝手に始まるので待ちます。

### インターネット接続をするための設定

この設定をしないと、後ほどインターネット接続画面から進むことができなくなります

このような画面が出てきたら、ShiftとF10を押してターミナルを起動します。

```
OOBE¥BYPASSNRO
```

を入力してEnter。

文字が打てない時はマウスを一度ターミナル内でクリックしましょう

勝手に再起動するので待ちます。

無事にこの画面がまた出てきたらおkです。

## Windows11のセットアップ

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-61.png)

日本を選択

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-62.png)

はいを選択

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-63.png)

スキップを選択

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-67.png)

- インターネットに接続していません

という青い文字が表示されるので、それをクリック

先ほどの、

[インターネット接続をするための設定](https://www.chickensblog.com/m1mac-win11/#toc19)

をやっていないと「インターネットに接続していません」という文字が出てきません。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-68.png)

- 制限された設定で続行

を選択

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-69.png)

ユーザー名の設定

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-70.png)

パスワードの設定

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-72.png)

セキュリティの質問を追加

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-74.png)

プライバシーの設定をします。自分は全部オフにしました。同意を押すと次に進みます。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-75.png)

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-76.png)

セットアップが終わるまで待ちます。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-77.png)

無事にWindows11が起動しました！

## インターネットに接続

ウィンドウの右上にある丸いボタンを選択し、

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-79.png)

- CD/DVD(ISO)
    - Change

を選択

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-80.png)

- spice-guest-tools-0.164.3.iso（バージョンによって名前が違います）

を選択します。

先ほどの

[インターネットに接続に必要なファイルのダウンロード](https://www.chickensblog.com/m1mac-win11/#toc8)

でダウンロードしたファイルを選択します。

少し時間が経つとドライブが認識されるので、エクスプローラーからドライブを開きます。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-82.png)

CDドライブを開くと

- spice-guest-tools

というファイルをダブルクリックで起動します。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-83.png)

はいを選択します。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-84.png)

Nextを選択

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-85.png)

I agreeを選択します

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-87.png)

インストールが始まります。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-88.png)

- Reboot now

を選択してfinishを選択すると再起動します。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-89.png)

再起動にかなり時間がかかりました（体感5分ほど）。

気長に待ちましょう。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-90.png)

再起動してログインします。

![](https://www.chickensblog.com/wp-content/uploads/2022/09/image-91.png)

インターネットに接続できました！

これで基本的な設定はすべて完了しました！おめでとうございます🎉

## まとめ

- Windows11をM1上で動かすことに成功した
- インターネットに接続することができた
- 普通に使うには申し分ないWindows11環境を作成することができた

## 最後に

何かわからないことやエラーなどが出たらコメントで教えてください。コメント、記事の共有が励みになります！

## 関連記事

[【革命！】M1MacでWindows11を無料&快適に動かす...zenn.dev](https://zenn.dev/teba_eleven/articles/aedc265d30e751) [Virtual Boxのインストール（環境構築）をしてみる【...はじめに今回はVirtualBoxの環境構築をやっていきます。Wind...www.chickensblog.com2022.04.07](https://www.chickensblog.com/virtual-box-install/) [【勉強方法も解説】Progateの周回ダメなのは嘘です【初心...初心者の方、Progateの周回ダメだと思ってませんか？初心者の方でも...www.chickensblog.com2021.05.21](https://www.chickensblog.com/progate/) [【Scratch】迷路を自動で作ってくれるプログラム&迷路探...はじめに今回は、Scratchで迷路を自動で生成するプログラムを作って...www.chickensblog.com2022.01.17](https://www.chickensblog.com/scratch-maze-generate/) [【Scratch】簡単なアクションゲームの作り方！リアルにジ...はじめに 今回は、Scratchで猫をリアルにジャンプさせる方法につい...www.chickensblog.com2021.12.15](https://www.chickensblog.com/kcc-cat-jump/) [【マイクラ革命】世界最速の計算機が従来の4倍もの計算速度を出...マイクラで数年前に作られた世界最速の計算機が、つい最近４倍もの計算処理...](https://www.chickensblog.com/minecraft-fastest-in-the-world-calculator/)