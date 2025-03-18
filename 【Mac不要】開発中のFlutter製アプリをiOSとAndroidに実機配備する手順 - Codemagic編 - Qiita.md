---
title: 【Mac不要】開発中のFlutter製アプリをiOSとAndroidに実機配備する手順 - Codemagic編 - Qiita
source: https://qiita.com/kami_teru/items/c7ed113d0ecdf7e48ff0
author:
  - "[[Qiita]]"
published: 2020-05-12
created: 2025-03-09
description: はじめにFlutterはクロスプラットフォーム対応ですので、作成したアプリはiOS, Android両方にリリースすることができます。ところが、WindowsではiOS向けのビルドができません。M…
tags:
  - プログラミング
---
この記事は最終更新日から3年以上が経過しています。

[@kami\_teru(Atsuteru Kamiya)](https://qiita.com/kami_teru)

- [Android](https://qiita.com/tags/android)
- [iOS](https://qiita.com/tags/ios)
- [Flutter](https://qiita.com/tags/flutter)
- [codemagic](https://qiita.com/tags/codemagic)

最終更新日 2020年05月12日投稿日 2020年05月09日

## はじめに

Flutterはクロスプラットフォーム対応ですので、作成したアプリはiOS, Android両方にリリースすることができます。ところが、WindowsではiOS向けのビルドができません。Macを持っていない人にはつらい事実ですね。そこで、この記事ではCodemagicというサービスを利用してiOS, Android両方にリリースする手順を紹介します。

## 前提

この記事は、以下に当てはまる人向けの iOS/Android 対応アプリを開発する手順を紹介します。

- 開発機はWindowsだ
- **Macを持っていない**
- Flutterで開発したい
- Apple Developer Programに既に登録している、または年間で約12,000円を支払えるクレジットカードまたはデビットカードを持っていて、支払い後に最大48時間待ってやるのも悪くない。※1

※1: 2020/03/25現在。

## 開発環境の前提

- AndroidStudioがインストールされていること（まだの方は、インストールをお願いします）
- Git for windowsがインストールされていること（まだの方は、インストールをお願いします）
- openSSL for windowsがインストールされていること（いかに手順のヒントを掲載しておきました）

## 補足:Windows用OpenSSLのインストールについて

OpenSSLは、オープンソースですが、公式ではソースコードのみが公開されています。  
従って、Windows用のバイナリは、公式サイト以外から入手する必要があります。

入手にあたり、以下の記事が参考になりましたので紹介します。  
[WindowsにOpenSSLをインストールして証明書を取り扱う（基本編） - @IT](https://www.atmarkit.co.jp/ait/articles/1601/29/news043.html)

## ソースコードの公開

この記事の手順で作成したソースコードはGithubで公開しています。併せてご参照ください。  
[https://github.com/atsuteru/flutter\_firebase\_0507/tree/Qiita-FlutterStartup-v1.0](https://github.com/atsuteru/flutter_firebase_0507/tree/Qiita-FlutterStartup-v1.0)

## 本文

## 開発環境の準備

### flutter開発用のディレクトリを作成する

私は以下のディレクトリを好んで使用します。

powershell

Copied!

```powershell
cd$Env:userprofilemkdirsourcemkdirsource\repos
```

※上記ディレクトリは、以下の手順でエクスプローラーで開けます。  
「Windows+R」(ファイル名を指定して実行)で以下を入力しOK。

Copied!

```text
%userprofile%\source\repos
```

### flutterSDKを入手する

Githubから入手します。

powershell

Copied!

```powershell
cd$Env:userprofile\source\reposgitclonehttps://github.com/flutter/flutter.git
```

## Flutterアプリを新規作成し、Githubにプッシュする

### 1) AndroidStudioで新規 Flutter プロジェクトを作成

1. Start a new Flutter project を選択  
[![Welcome to Android Studio 2020_05_03 14_29_48.png](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2F7119ba8f-bab6-0d1e-12ca-9739b4e1ae67.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=cbb335ec718ca0583bb3965d7e2a3ad0)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2F7119ba8f-bab6-0d1e-12ca-9739b4e1ae67.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=cbb335ec718ca0583bb3965d7e2a3ad0)
2. Flutter Application を選択  
[![Welcome to Android Studio 2020_05_03 14_30_02.png](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2F4a52bff7-0104-c718-01af-5218e99eabf9.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=337605c59cbfe3f74419b7d63895cdae)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2F4a52bff7-0104-c718-01af-5218e99eabf9.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=337605c59cbfe3f74419b7d63895cdae)
3. Projectの情報と、Flutter sdkのチェックアウトディレクトリを指定する  
[![Welcome to Android Studio 2020_05_03 14_30_25.png](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2Ff02cdbee-098a-5078-c1bf-8f991ac4267b.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=95db89eaa451459280507abe8d126c29)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2Ff02cdbee-098a-5078-c1bf-8f991ac4267b.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=95db89eaa451459280507abe8d126c29)
4. パッケージ名を指定する。AndroidXは有効にしておく  
[![Welcome to Android Studio 2020_05_03 14_30_36.png](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2F0828e4d4-2bc0-c507-0dd1-ede0cb097d7c.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=35456bf55825060549b8392cd6f28c74)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2F0828e4d4-2bc0-c507-0dd1-ede0cb097d7c.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=35456bf55825060549b8392cd6f28c74)
5. すると次のようなワークスペースが作成されます  
[![flutter_firebase_0503 [C__Users_kami_teru_source_repos_flutter_firebase_flutter_firebase_0503] - ..._lib_main.dart [flutterfirebase0503] - Android Studio 2020_05_03 14_32_08.png](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2Ff2545680-1dc2-de3b-8027-2603b927c240.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=c8279fd567dd885548a8420d78269647)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2Ff2545680-1dc2-de3b-8027-2603b927c240.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=c8279fd567dd885548a8420d78269647)

### 2) Flutter プロジェクトの`.gitignore`を調整

- ルートディレクトリの`.gitignore`に以下を追加 - 参考: [What not to commit - Dart](https://dart.dev/guides/libraries/private-files)

/.gitignore

Copied!

```text
pubspec.lock
```

### 3) Githubリポジトリを作成し、pushする

Githubアカウントを持っていない人は、作成しましょう。（無料で作れます）  
※Github以外でも、Codemagicが連携できるリポジトリならOKですが、その説明はこの記事では割愛します。

Githubリポジトリの作成手順は、ここでは割愛します。  
Githubリポジトリの作成後、プッシュまでの流れは、コマンドだと次のような感じです。

powershell

Copied!

```powershell
cd$Env:userprofile\source\repos\flutter_firebase\flutter_firebase_0503gitinitgitadd.gitcommit-m"New flutter project generated by AndroidStudio"gitremoteaddoriginhttps://github.com/atsuteru/flutter_firebase_0503.gitgitpush-uoriginmaster
```

## FlutterアプリをCodemagicでビルドする

### 1) CodemagicでGithubリポジトリを初回ビルドする

Codemagicのアカウントがない場合は、Githubアカウントと連携させる形で作成します。（無料で作れます）  
Codemagicのアカウントがある場合は、Githubアカウントの連携を追加してください。  
その手順は、ここでは割愛します。

Githubアカウントの連携ができたら、[Appsページ](https://codemagic.io/apps)に、作成したGithubリポジトリが表示されます。

[![Applications overview - Codemagic - Mozilla Firefox 2020_05_07 19_33_45.png](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2F881d5fab-7667-94ff-658f-5e70820ee885.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=74a424e072e98f3666c415e73c8dca36)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2F881d5fab-7667-94ff-658f-5e70820ee885.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=74a424e072e98f3666c415e73c8dca36)

そのリポジトリの`Start your first build`ボタンを押下しましょう。すると、Codemagicでのビルド設定が自動的に作成され、初回ビルドが始まります。

ここでビルドの結果がエラーになる場合は、バージョン、環境、サービスのいずれかに問題が起こっています。  
私は、以下の問題にあたったことがあります。

- サービス: iOSビルドが、関連ライブラリ(dependency)のダウンロードに失敗したことが原因で失敗。時間を空けて再実行することで解消した。

### 2) 端末にリリースするために必要な、署名用のあれこれを行う

#### 2-1) Android向け

初回ビルドの結果を待っている間に、アプリを署名するためのキーストアを作成しましょう。

- Androidアプリを実機で動作させるためには、署名されたアプリケーションパッケージが必要です。
- その署名には秘密鍵が必要です。
- また実機にインストールするためには公開鍵の配付が必要です。
- 公開鍵の作成には、証明書が必要です。
- キーストアとは、上記に登場した「秘密鍵」「公開鍵」「証明書」を格納できる『ハコ』だと思ってください。

作成するためには、コマンドラインを使用します。  
以下の手順で作成することができます。

powershell

Copied!

```powershell
# インストールしたOpenSSLのbinフォルダにパスを通す# 実際にインストールしたパスを指定すること。先頭の";"を忘れないこと！$Env:Path+=";C:\Program Files\OpenSSL-Win64\bin\"# Java KeyStore(jks)形式のキーストアを作成する# この例では、次のように設定しています。※実際は安全なパスワードを使用しましょう！# キーストアファイル名: flutter_firebase_0503.jks, キーストアパスワード: kami_teru, キー名: flutter_firebase_0503_key, キーパスワード: kaim_teru, 有効期間: 365日keytool-genkey-v-keystoreflutter_firebase_0503.jks-storepasskami_teru-aliasflutter_firebase_0503_key-keypasskami_teru-keyalgRSA-validity365姓名は何ですか。［Unknown］:kami_teru組織単位名は何ですか。［Unknown］:組織名は何ですか。［Unknown］:kami_teru都市名または地域名は何ですか。［Unknown］:都道府県名または州名は何ですか。［Unknown］:この単位に該当する2文字の国コードは何ですか。［Unknown］:JPCN=kami_teru,OU=Unknown,O=kami_teru,L=Unknown,ST=Unknown,C=JPでよろしいですか。［いいえ］:Y365日間有効な2,048ビットのRSAのキー・ペアと自己署名型証明書(SHA256withRSA)を生成していますディレクトリ名:CN=kami_teru,OU=Unknown,O=kami_teru,L=Unknown,ST=Unknown,C=JP［flutter_firebase_0503.jksを格納中］# キーストアから、キーに対する証明書を取り出す。keytool-export-aliasflutter_firebase_0503_key-fileflutter_firebase_0503_key.cer-keystoreflutter_firebase_0503.jksキーストアのパスワードを入力してください:証明書がファイル<flutter_firebase_0503_key.cer>に保存されました# キーストアを、テキスト形式に変換しておく（後で使います）opensslenc-base64-influtter_firebase_0503.jks-outflutter_firebase_0503.base64
```

#### 2-2) iOS向け

iOS向けの署名に必要な一式は、Codemagic と Apple Developer Program のアカウントを連携させることで自動的に作成してもらえます。但しその前に、リリースするiOSの実機を、Apple Developer Programに登録しておく必要があります。

[Deviceのページ](https://developer.apple.com/account/resources/devices/list)から、実機のUUIDを登録しておきましょう。

※UUIDは、iPhoneの場合はiTunesに接続すると調べることができます。その他の方法もいくつかあるようです。参考：[iPhone XSシリーズからのUDID・識別子の確認方法 - @takashings](https://qiita.com/takashings/items/f4f96d8f948e14cd98d9)

### 3) Codemagicでリリースビルドする

さて、もうCodemagicの初回ビルドは終わった頃でしょうか。

[![Applications overview - Codemagic - Mozilla Firefox 2020_05_07 20_03_09.png](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2F33cd4269-62d8-ea9f-3091-3f7dd688fd3d.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=17205287da62323b3da18b36a6dfc23a)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2F33cd4269-62d8-ea9f-3091-3f7dd688fd3d.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=17205287da62323b3da18b36a6dfc23a)

終わったみたいですね！各ビルドのStepとも、成功しているようです。しかし、このビルドの結果は、実機にインストールすることができません。アプリに署名をしていないからですね。

では、リリースビルドを行い、アプリに署名を行うための設定をしていきましょう。

- iOS向けには、Apple Developer Programのアカウントが必要です
- Android向けには、先ほどの手順で作成したキーストアファイルが必要です。

なお、ここで紹介する手順は以下の記事を参考にさせていただきました。ありがとうございます。

- [Codemagicの設定手順＆ハマりそうなところをまとめてみた - @yukitaka13-1110](https://qiita.com/yukitaka13-1110/items/2b4fb8a25c1559f3e278)

以下、Codemagicのアプリの設定ページ（歯車のアイコンで飛べる）で、各セクションを設定します。こんなページです。  
[![App settings - Google Chrome 2020_05_09 16_51_28.png](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2Fcd5166eb-f152-5330-3045-e1e80465290d.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=651439e8a81813072254f4b82070b054)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2Fcd5166eb-f152-5330-3045-e1e80465290d.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=651439e8a81813072254f4b82070b054)

先に、注意点をまとめておきます。

- 注意１）各セクションの編集後、必ず「Save」ボタンを押しましょう。
- 注意２）入力がうまくできないときは、セクションを閉じたり開いたりしなおしてみましょう。

では以下、各セクションを設定しましょう。記載のない箇所は、デフォルトのままで構いません。

#### Build triggers

- `Trigger on push`にチェックを付ける

#### Environment variables

以下の環境変数を追加する。  
一つ入力するごとに、「Add」ボタンを押し忘れないようにしましょう。

- FCI\_KEYSTORE\_FILE = `flutter_firebase_0503.base64ファイルの内容` ※全選択＆コピー＆貼り付けを実行。改行も含めること
- FCI\_KEYSTORE\_PASSWORD = `kami_teru` ※キーストアに設定したパスワード
- FCI\_KEY\_ALIAS = `flutter_firebase_0503_key` ※キーストアの作成時に指定した秘密鍵の別名
- FCI\_KEY\_PASSWORD = `kami_teru` ※キーストアの作成時に指定した秘密鍵のパスワード

#### Post-clone script

`Dependency caching`の下の「＋」をクリックすると出現します。  
以下のスクリプトをそのままコピペしてください。

Copied!

```sh
#!/usr/bin/env sh
set -e # exit on first failed commandset
echo $FCI_KEYSTORE_FILE | base64 --decode > $FCI_BUILD_DIR/keystore.jks
```

#### Build

- Build for platforms : Android, iOSを選択する
- Mode: Releaseを選択する

#### Publish

1. Android code signing

- Keystore: `flutter_firebase_0503.jks` ※ファイルをアップロード。
- Keystore password: `kami_teru` ※キーストアに設定したパスワード
- Key alias: `flutter_firebase_0503_key` ※キーストアの作成時に指定した秘密鍵の別名
- Key password: `kami_teru` ※キーストアの作成時に指定した秘密鍵のパスワード
- Enable Android code signing: チェックを付ける

1. iOS code signing

- Select code signing method: `Automatic`を選択
- Apple Developer Programのアカウントを設定
- Provisioning profile type: `Development`を選択
- Bundle identifier (optional): `test.kamiteru.flutterfirebase0503` ※1

※1 android\\app\\src\\profile\\AndroidManifest.xml ファイルの packageに設定されているものを入力する

最後に、設定ページの最上部にある「Start new Build」ボタンを押し、ビルドを行いましょう。  
この設定以降のビルドはすべて、リリースビルドになります。

※この時、以下のページが表示されたら、`Start new build`を選択しましょう。  
※Mac Proを使えばビルドはもっと早いよ！という紹介のページです。アカウント作成後は数回、Mac Proでビルドすることもできます。

[![Applications overview - Codemagic - Mozilla Firefox 2020_05_07 20_19_44.png](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2Fdc5706e5-8829-cc7f-3da6-06b1a95af3e8.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=95df95a16d6236c2241cbaa9ce49806d)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2Fdc5706e5-8829-cc7f-3da6-06b1a95af3e8.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=95df95a16d6236c2241cbaa9ce49806d)

## Flutterアプリを端末にインストールする

リリースビルドが行われているうちに、端末に証明書の取り込みをやっておきましょう。

- この作業は Android端末 のみ必要です。
- iOS端末は、Apple Developer Programに自端末を登録してある仕掛けにより、アプリ側に「どの端末にインストールできるか」が埋め込まれているため、この作業は不要です。

### Android端末への証明書のインストール

先の手順で作成した`flutter_firebase_0503_key.cer`を、メール等を経由してAndroid端末に送りましょう。  
メールの場合、受信したメールに添付された`flutter_firebase_0503_key.cer`をタップして開き、証明書名にアプリ名を入力してOKしましょう。

[![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2Faa0305a3-3006-8f3d-28a7-8519e0e71e00.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=46b47d3528efe0569c57fb394fcf87c0)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2Faa0305a3-3006-8f3d-28a7-8519e0e71e00.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=46b47d3528efe0569c57fb394fcf87c0)

さて、そうこうしているうちに、Codemagicでのリリースビルドが完了しているのではないでしょうか。

### Codemagicからのメールをチェック

ビルドが成功/失敗すると、Codemagicから次のようなメールが届きます。  
※もし届かない場合は、Codemagicのメールの設定を確認しましょう。

[![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2Fd67b6bc5-ce2c-392c-73c3-1084576d2812.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=8dbf8d467a5a20588f781bc7746e0ac0)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2Fd67b6bc5-ce2c-392c-73c3-1084576d2812.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=8dbf8d467a5a20588f781bc7746e0ac0)

### Androidへのインストール

Androidへのインストールは、次の手順で行います。

1. `app-release.apk`のInstallボタンをタップ  
→ダウンロード

[![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2Fc8aa4a84-3cc2-050a-e2e6-bdee3bd10aed.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=bf3a1279756eec09ac72d854e93cb91b)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2Fc8aa4a84-3cc2-050a-e2e6-bdee3bd10aed.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=bf3a1279756eec09ac72d854e93cb91b) 1. ダウンロードした\`\`\`app-release.apk\`\`\`を実行  
※内部ストレージのDownloadフォルダに保存されています  
[![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2F484193d7-70d6-74e7-118c-d17ea567bf95.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=eafc97a812e261f4417a9409d5f995d9)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2F484193d7-70d6-74e7-118c-d17ea567bf95.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=eafc97a812e261f4417a9409d5f995d9) 1. 内部ストレージアプリによる「提供元不明なアプリ」のインストール許可の確認が出るので、許可するよう設定します。  
[![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2F6cc7ea4b-28e4-d29b-53e4-ae4dca2521b4.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=463d2181b0253b8a44d624155b7b5dac)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2F6cc7ea4b-28e4-d29b-53e4-ae4dca2521b4.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=463d2181b0253b8a44d624155b7b5dac) [![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2Fe5378b85-cb28-3d29-504f-3ffa3a9e4f10.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=31bc3b897a442d68e17afa7068fc4c8f)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2Fe5378b85-cb28-3d29-504f-3ffa3a9e4f10.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=31bc3b897a442d68e17afa7068fc4c8f) 1. 確認画面でインストールを選択  
[![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2Fc8feba9e-a50d-a504-daf7-a9f86dfbbc45.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=35457ff30de2878a63070f3cba2907c2)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2Fc8feba9e-a50d-a504-daf7-a9f86dfbbc45.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=35457ff30de2878a63070f3cba2907c2) [![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2Fa1116340-62c8-b68b-44f0-2ff98f585e9f.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=a7053d64f41f00bd3581ce83466342fa)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2Fa1116340-62c8-b68b-44f0-2ff98f585e9f.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=a7053d64f41f00bd3581ce83466342fa) 1. もしGoogle Playの警告が出た場合は、アプリ名が自作のものであることを確認し、\`\`\`INSTALL ANYWAY\`\`\`を選択しましょう  
[![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2F4d35d0a2-895c-cd3d-3771-7bd2291be8a5.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=9dc4917be217f22a7fb8686ed276a04d)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2F4d35d0a2-895c-cd3d-3771-7bd2291be8a5.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=9dc4917be217f22a7fb8686ed276a04d) 1. Androidで動作することが確認できました  
[![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2Fb54f7aad-3ac3-849e-37eb-48658c09725f.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=a50df6829bcea03396f70fc6f90beef5)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2Fb54f7aad-3ac3-849e-37eb-48658c09725f.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=a50df6829bcea03396f70fc6f90beef5)

### iOSへのインストール

iOSへのインストールは、次の手順で行います。

1. `flutterfirebase0503.ipa`のInstallボタンをタップ  
→確認画面でインストールを選択

[![unnamed.jpg](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2Faad389cf-b203-d3e9-c6d3-2534ce7c9800.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=60a2db680e58d2faa6751cb5b6b43ed9)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2Faad389cf-b203-d3e9-c6d3-2534ce7c9800.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=60a2db680e58d2faa6751cb5b6b43ed9) 1. iOSで動作することが確認できました  
[![unnamed (1).jpg](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2F60fcfe6a-38e3-0856-46c4-736eb1d5ecdc.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=f7fd498406f882b1b07dbea94fd68ac3)](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F109362%2F60fcfe6a-38e3-0856-46c4-736eb1d5ecdc.jpeg?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=f7fd498406f882b1b07dbea94fd68ac3)

## おわりに

以上で、開発中のFlutter製アプリをiOSとAndroidに実機配備できましたね！

もし良ければ、以下の続編記事も参考に開発を進められてください。

- [【Mac不要】開発中のFlutter製アプリを仲間のiOS端末に実機配備する手順 - Codemagic&TestFlight編](https://qiita.com/kami_teru/items/6d5c9b24f711f1270697)
- [【Mac不要】FlutterアプリにFirebase SDKを組み込んでiOSとAndroidに実機配備する手順 - Codemagic編](https://qiita.com/kami_teru/items/d3b72f5c0aa97e6c1c08)

この記事が、一人でも多くの方がFlutterを始めてみるきっかけになると幸いです。

[130](https://qiita.com/kami_teru/items/c7ed113d0ecdf7e48ff0/likers)

いいねしたユーザー一覧へ移動

108

[0](https://qiita.com/kami_teru/items/#comments)