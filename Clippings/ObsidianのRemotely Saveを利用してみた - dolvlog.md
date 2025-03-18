---
title: ObsidianのRemotely Saveを利用してみた - dolvlog
source: https://roodolv.dev/posts/2024/09/obsidian-remotely-save/
author:
  - "[[dolvlog]]"
published: 2024-09-21
created: 2025-03-19
description: 2か月ほどブログ更新が滞ってしまっていたので久々に更新要約 表題の通りObsidianのRemotely Saveプラグインを試してみようと思っていたので、今回色々やってみたEncryption Passwordは一番最初に設定すること(重要) Cloudflare R2とDropboxを試した...
tags:
  - Obsidian
"#Cloudflare R2":
---
### 要約
[[Obsidianが大学生活を変える! 学生必見の活用術 - Qiita]]
表題の通り[Obsidian](https://obsidian.md/)の[Remotely Save](https://github.com/remotely-save/remotely-save)プラグインを試してみようと思っていたので、今回色々やってみた

- Encryption Passwordは一番最初に設定すること(重要)
- Cloudflare R2とDropboxを試したがサービス間の同期速度差は体感上なし
- それよりも端末間のスペック差の方が同期速度への影響が大きいと思われる
- スマホからはRead Onlyで使うことに

### ObsidianのRemotely Saveについて

これはObsidianを利用している人には有名なプラグインで、要するにMarkdownなどの **メモを暗号化してクラウドストレージに保管し、端末間で同期してくれる** という優れものだ

暗号化は **End-to-end(E2E) encryption** で行われ、暗号化方式はRClone Crypt(デフォルト)かOpenSSL encかの二択となっている

[GitHub公式リポジトリの説明](https://github.com/remotely-save/remotely-save?tab=readme-ov-file#features)にもある通り、AWSのS3やDropboxやWebDAVなど様々なサービス・機能が同期用ストレージとして利用可能なのだが、今回自分は

- Dropbox
- Cloudflare R2 (S3準拠)

の2つでテストしてみた

プラグインのインストール方法などは省略

### Remotely Saveを利用する際の注意点

#### 暗号化パスワードについて

もし平文ではなく **暗号化されたメモ** をクラウドストレージに置きたい場合、必ず **一番初めに「Encryption Password」を設定** することをおすすめする

当然だが、クラウドサービス利用時にAPIエンドポイントのURLやアクセスキーIDなどの必要情報を先に一通り入力し、そのまま同期してしまうと **メモが平文のままアップロードされてしまう**

パスワード設定項目はRemotely Save設定画面の最上部より少し下へスクロールした辺りにあるので注意

![](https://roodolv.dev/posts/img/2024-09/remotely-save-config01.png)

上記画像にも書いてあるように「Confirm」をクリックしてパスワードを設定しないと有効にならない点にも注意

また、Remotely Saveの設定画面最下部に「Reset」ボタンがあるが、このResetを実行する度にプラグインを再度読み込むらしいので、自分はResetした場合には一応Encryption PasswordのConfirmを再度実行してから同期することにしている

#### 従量課金に注意

連携するクラウド系サービスによっては従量課金になっている点に注意が必要だ

例えば今回利用した **Cloudflare R2も従量課金** となっている

- 公式資料: [https://developers.cloudflare.com/r2/pricing/](https://developers.cloudflare.com/r2/pricing/)

具体的には、下記の通り

- ストレージ: **10GB/月** まで無料
- ClassA操作(≒書き込み): **100万回/月** まで無料
- ClassB操作(≒読み込み): **1000万回/月** まで無料
- エグレス: 無料

なお厳密なClassA操作とClassB操作の内訳は下記の通りらしい

> Class A Operations include `ListBuckets`, `PutBucket`, `ListObjects`, `PutObject`, `CopyObject`, `CompleteMultipartUpload`, `CreateMultipartUpload`, `LifecycleStorageTierTransition`, `ListMultipartUploads`, `UploadPart`, `UploadPartCopy`, `ListParts`, `PutBucketEncryption`, `PutBucketCors` and `PutBucketLifecycleConfiguration`.

> Class B Operations include `HeadBucket`, `HeadObject`, `GetObject`, `UsageSummary`, `GetBucketEncryption`, `GetBucketLocation`, `GetBucketCors` and `GetBucketLifecycleConfiguration`.

### Remotely SaveでCloudflare R2を利用する方法

一応メモしておく

#### Cloudflare R2用に支払い手段を登録する

Cloudflareアカウントを持っていない場合はここで作成する必要がある

既にCloudflareアカウントがある場合はCloudflareのログイン済みダッシュボード(Dashboard)から左側の「R2」を選択すればR2サービスの利用開始画面に移動する

あとは指示通りにクレジットカードかPayPalの登録をすればR2サービスが利用できるようになる

[以前の記事](https://roodolv.dev/posts/2024/02/domain-transfer-to-cloudflare)でも書いたように、自分はドメイン管理やリバースプロキシなどでCloudflareは既に利用していたので、そのままPayPalを支払い手段としてR2を利用することにした

#### R2用のバケットを作成する

R2を利用するために **バケット(Bucket)** を作成する

URLの一部になるらしいのでハイフンなどで繋げつつ適当な名前で作ってみた

- 名前: `obsidian-remotely-save`
- 位置情報(リージョン): **自動**
- デフォルトのストレージクラス: **Standard**

にしておいた

作成したバケットの設定画面を見ると、このようにAPIエンドポイント用のURLが表示される(S3 APIの部分) ![](https://roodolv.dev/posts/img/2024-09/remotely-save-config02.png)

`https://`から`cloudflarestorage.com`まで(末尾スラッシュなし)がRemotely Saveプラグインに求められる部分なので一応メモしておくと良い

ちなみにリージョンは自動で「アジア太平洋(APAC)」になった

#### APIアクセス用トークンを作成する

トークン名は自分が分かればいいので適当なものにする

権限とバケット指定は下記の通りにした

- 権限: **オブジェクト読み取りと書き込み**
- バケットの指定: **特定のバケットにのみ適用**
- 作成したバケット名`obsidian-remotely-save`を指定

![](https://roodolv.dev/posts/img/2024-09/remotely-save-config03.png)

他の方の記事では「管理者読み取りと書き込み」にしないとダメだったという意見を見たが、自分の環境では「オブジェクト読み取りと書き込み」で十分に同期可能だった(環境によるのかも知れない)

#### アクセスキーIDとシークレットアクセスキーをメモしておく

APIトークンを作成すると、 **一度だけ** 画面上にアクセスキーIDとシークレットアクセスキーが表示されるので必ずメモしておく

![](https://roodolv.dev/posts/img/2024-09/remotely-save-config04.png)

これらの情報はあとでRemotely Saveプラグインの設定時に必要不可欠なので絶対に見落とさないようにしたい

#### ObsidianのRemotely Save設定画面から必要事項を入力

あとは下記の通り、ObsidianのプラグインRemotely Save設定画面から各種情報を入力することで同期の準備が完了する

- Choose A Remote Service: **S3 or compatible**
- Endpoint
- Region
- Access Key ID
- Secret Access Key
- Bucket Name

![](https://roodolv.dev/posts/img/2024-09/remotely-save-config05.png)

Regionは`us-east-1`にしておくと良い、と書いてあるが自分は`auto`にしておいた

#### Remotely Saveで同期開始

これで準備完了だが、念のためRemotely Save設定画面から **Check Connectivity** のCheckボタンをクリックして同期可能かどうか確認しておくと良い

必要事項入力後、Obsidianのコマンドパレット上から「Remotely Save: start sync」を選択するか、左側のリボンから「Remotely Save」の矢印アイコンをクリックするとその場で同期が開始される

あとは別端末のObsidianの方でも同様にRemotely Saveプラグインの設定をし、同じ暗号化パスワードを入れれば暗号化されたデータが復号されて保存・同期される

### Remotely Saveの使い心地など

#### 自分のObsidian環境について

自分のObsidianには凡そ6000超のファイルが含まれており、うち2000ほどは画像・PDFなどのファイル群、残り4000ほどがMarkdownファイルという構成になっている

#### 問題発生: 同期の速度が端末ごとに大きく異なる

上記の通りファイル数がやや多め(？)だったことが災いしたのか、スマホから同期しようとすると **数行のファイル変更差分を同期するだけで10～40分かかってしまう** ことが今回分かった

例えばPC上からの同期は **数秒で終わる** のに、iPhone SE(第二世代)などで同期を行うと数十分かかったりする

#### いろいろ検証してみた

原因を特定しようと思い、

- 連携するクラウドサービス(DropboxとCloudflare R2)を切り替えたり
- スマホを再起動してメモリを空けたり
- Vault内にある全画像の解像度をリサイズするなどしてバイナリ系の総ファイルサイズを半減させたり
- ネットワークを切り替えてみたり
- etc

様々な検証をしてみた(下記はファイルサイズを半分に減らした時のR2ストレージの推移)

![](https://roodolv.dev/posts/img/2024-09/remotely-save-config06.png)

しかしどれも効果は乏しく、利用するサービスやネットワークの速度、ファイルサイズも直接的な要因ではないようだった

むしろ、ローカルの端末スペックに依存している(？)様子だった

やはりiPhone SE(第二世代)のロースペックぶりが足を引っ張っているのだろうか……？

#### 同期速度低下の原因について推測

重要なのが、クラウドサービスにおいてDropbox(のAPI)を使う場合とCloudflare R2を使う場合の **速度差は体感上ほぼ無かった** ということだ

どちらを使った場合もPCからのアップロードとダウンロード(fetch)に関してはスムーズに済む一方、スマホからだとどうしてもモタついてしまうことが分かった

恐らくだが、動画ファイルなど比較的ファイルサイズの大きめ[^1]なバイナリファイルがObsidianのVault内にある場合に、Remotely Saveプラグイン本体がローカルキャッシュ(DB)とクラウド上のオブジェクトとの差分を走査＆検出しようとするが、ロースペックのスマホだとそれをこなす能力が足りず、結果として遅くなっているのでは……と推測している

あるいは、TypeScript製であるRemotely SaveプラグインがiOSのObsidianで動作する際、JSやTSの(Webブラウザ/Electron上における)動作をエミュレートしているので遅くなっているとか、直接ネイティブコードのようなものに変換しているので遅くなっているとか、色々と考えられるが……

詳細は今回調査していないので分からない。いずれ調査するかも知れない

#### ReadOnlyで使うならまぁまぁの使い心地

とにかく自分の環境だと **スマホからの同期が実用レベルにない速度** となってしまった為、現時点では双方向のWriteは諦め、スマホの方からはRead Only用途で使うことにした

クラウドサービスについてはCloudflare R2もDropboxも両方利用可能な状態にしてあるが、今の所Dropboxを利用している

とは言え、Read Onlyでもやはり **Vault全体を暗号化し、クラウドで同期できるのは非常に有難い**

スマホ版Obsidianアプリはまだまだ発展途上という感じはするが、現時点で既に使い心地は十分良好なので今後にも期待したい

[^1]: とは言っても自分のVault内で最大のファイルサイズは28.1MBで、10MB以上のファイルも全部で6つしかないのだが