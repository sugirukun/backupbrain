---
title: Obsidian Sync を無料で使う方法! (有料プランは不要) | HackerNoon
source: https://hackernoon.com/lang/ja/%E6%9C%89%E6%96%99%E3%83%97%E3%83%A9%E3%83%B3%E3%81%AA%E3%81%97%E3%81%A7Obsidian-Sync%E3%82%92%E7%84%A1%E6%96%99%E3%81%A7%E8%A1%8C%E3%81%86%E6%96%B9%E6%B3%95
author: 
published: 
created: 2025-03-14
description: このガイドでは、GitHub と Git を使用して、費用をかけずにメモを同期させる方法について説明します。
tags:
  - obsidian
  - github
---
1,118 測定値

1,118 測定値

に Vladislav Guzey5 分 read2025/02/20

Read this story in a terminal

Print this story

[JA

この物語を日本語で読んでください！

](https://hackernoon.com/lang/ja/%E6%9C%89%E6%96%99%E3%83%97%E3%83%A9%E3%83%B3%E3%81%AA%E3%81%97%E3%81%A7Obsidian-Sync%E3%82%92%E7%84%A1%E6%96%99%E3%81%A7%E8%A1%8C%E3%81%86%E6%96%B9%E6%B3%95)[EN

Read this story in the original language, English!

](https://hackernoon.com/how-to-obsidian-sync-for-free-no-paid-plan-required)[BN

এই গল্পটি বাংলায় পড়ুন!

](https://hackernoon.com/lang/bn/%E0%A6%95%E0%A6%BF%E0%A6%AD%E0%A6%BE%E0%A6%AC%E0%A7%87-%E0%A6%AC%E0%A6%BF%E0%A6%A8%E0%A6%BE%E0%A6%AE%E0%A7%82%E0%A6%B2%E0%A7%8D%E0%A6%AF%E0%A7%87-%E0%A6%85%E0%A6%AC%E0%A6%B8%E0%A6%BF%E0%A6%A1%E0%A6%BF%E0%A6%AF%E0%A6%BC%E0%A6%BE%E0%A6%A8-%E0%A6%B8%E0%A6%BF%E0%A6%99%E0%A7%8D%E0%A6%95-%E0%A6%95%E0%A6%B0%E0%A6%AC%E0%A7%87%E0%A6%A8-%E0%A6%95%E0%A7%8B%E0%A6%A8-%E0%A6%AA%E0%A7%87%E0%A6%87%E0%A6%A1-%E0%A6%AA%E0%A7%8D%E0%A6%B2%E0%A7%8D%E0%A6%AF%E0%A6%BE%E0%A6%A8%E0%A7%87%E0%A6%B0-%E0%A6%AA%E0%A7%8D%E0%A6%B0%E0%A6%AF%E0%A6%BC%E0%A7%8B%E0%A6%9C%E0%A6%A8-%E0%A6%A8%E0%A7%87%E0%A6%87)[ES

Lee esta historia en Español!

](https://hackernoon.com/lang/es/como-sincronizar-obsidian-de-forma-gratuita-sin-necesidad-de-un-plan-de-pago)[HI

इस कहानी को हिंदी में पढ़ें!

](https://hackernoon.com/lang/hi/%E0%A4%93%E0%A4%AC%E0%A5%8D%E0%A4%B8%E0%A5%80%E0%A4%A1%E0%A4%BF%E0%A4%AF%E0%A4%A8-%E0%A4%B8%E0%A4%BF%E0%A4%82%E0%A4%95-%E0%A4%AE%E0%A5%81%E0%A4%AB%E0%A5%8D%E0%A4%A4-%E0%A4%AE%E0%A5%87%E0%A4%82-%E0%A4%95%E0%A5%88%E0%A4%B8%E0%A5%87-%E0%A4%95%E0%A4%B0%E0%A5%87%E0%A4%82%2C-%E0%A4%95%E0%A5%8B%E0%A4%88-%E0%A4%AD%E0%A5%81%E0%A4%97%E0%A4%A4%E0%A4%BE%E0%A4%A8-%E0%A4%AF%E0%A5%8B%E0%A4%9C%E0%A4%A8%E0%A4%BE-%E0%A4%95%E0%A5%80-%E0%A4%86%E0%A4%B5%E0%A4%B6%E0%A5%8D%E0%A4%AF%E0%A4%95%E0%A4%A4%E0%A4%BE-%E0%A4%A8%E0%A4%B9%E0%A5%80%E0%A4%82-%E0%A4%B9%E0%A5%88)[KY

Бул окуяны кыргызча окуңуз!

](https://hackernoon.com/lang/ky/%D0%B1%D0%B5%D0%BA%D0%B5%D1%80-%D0%BE%D0%B1%D1%81%D0%B8%D0%B4%D0%B8%D0%B0%D0%BD-%D1%81%D0%B8%D0%BD%D1%85%D1%80%D0%BE%D0%BD%D0%B4%D0%BE%D1%88%D1%82%D1%83%D1%80%D1%83%D1%83-%D2%AF%D1%87%D2%AF%D0%BD-%D1%8D%D1%87-%D0%BA%D0%B0%D0%BD%D0%B4%D0%B0%D0%B9-%D0%B0%D0%BA%D1%8B-%D1%82%D3%A9%D0%BB%D3%A9%D0%BD%D2%AF%D2%AF%D1%87%D2%AF-%D0%BF%D0%BB%D0%B0%D0%BD-%D1%82%D0%B0%D0%BB%D0%B0%D0%BF-%D0%BA%D1%8B%D0%BB%D1%8B%D0%BD%D0%B1%D0%B0%D0%B9%D1%82)[NE

यो कथा नेपालीमा पढ्नुहोस्!

](https://hackernoon.com/lang/ne/%E0%A4%AD%E0%A5%81%E0%A4%95%E0%A5%8D%E0%A4%A4%E0%A4%BE%E0%A4%A8-%E0%A4%97%E0%A4%B0%E0%A4%BF%E0%A4%8F%E0%A4%95%E0%A5%8B-%E0%A4%AF%E0%A5%8B%E0%A4%9C%E0%A4%A8%E0%A4%BE-%E0%A4%86%E0%A4%B5%E0%A4%B6%E0%A5%8D%E0%A4%AF%E0%A4%95-%E0%A4%AA%E0%A4%B0%E0%A5%8D%E0%A4%A6%E0%A5%88%E0%A4%A8%2C-%E0%A4%A8%E0%A4%BF%3A%E0%A4%B6%E0%A5%81%E0%A4%B2%E0%A5%8D%E0%A4%95-%E0%A4%93%E0%A4%AC%E0%A5%8D%E0%A4%B8%E0%A4%BF%E0%A4%A1%E0%A4%BF%E0%A4%AF%E0%A4%A8-%E0%A4%B8%E0%A4%BF%E0%A4%99%E0%A5%8D%E0%A4%95-%E0%A4%95%E0%A4%B8%E0%A4%B0%E0%A5%80-%E0%A4%97%E0%A4%B0%E0%A5%8D%E0%A4%A8%E0%A5%87)[FA-AF

این داستان را به زبان دری بخوانید!

](https://hackernoon.com/lang/fa-AF/%D9%86%D8%AD%D9%88%D9%87-%D9%87%D9%85%DA%AF%D8%A7%D9%85-%D8%B3%D8%A7%D8%B2%DB%8C-%D8%A7%D8%A8%D8%B3%DB%8C%D8%AF%DB%8C%D9%86-%D8%A8%D9%87-%D8%B5%D9%88%D8%B1%D8%AA-%D8%B1%D8%A7%DB%8C%DA%AF%D8%A7%D9%86-%D8%A8%D8%AF%D9%88%D9%86-%D9%86%DB%8C%D8%A7%D8%B2-%D8%A8%D9%87-%D8%A8%D8%B1%D9%86%D8%A7%D9%85%D9%87-%D9%BE%D9%88%D9%84%DB%8C)[TL

Basahin ang kwentong ito sa Filipino!

](https://hackernoon.com/lang/tl/kung-paano-mag-sync-ng-obsidian-nang-libre-nang-walang-bayad-na-plano)[UK

Читайте цю історію українською!

](https://hackernoon.com/lang/uk/%D1%8F%D0%BA-%D1%81%D0%B8%D0%BD%D1%85%D1%80%D0%BE%D0%BD%D1%96%D0%B7%D1%83%D0%B2%D0%B0%D1%82%D0%B8-obsidian-%D0%B1%D0%B5%D0%B7%D0%BA%D0%BE%D1%88%D1%82%D0%BE%D0%B2%D0%BD%D0%BE%2C-%D0%BF%D0%BB%D0%B0%D1%82%D0%BD%D0%B8%D0%B9-%D0%BF%D0%BB%D0%B0%D0%BD-%D0%BD%D0%B5-%D0%BF%D0%BE%D1%82%D1%80%D1%96%D0%B1%D0%B5%D0%BD)[FI

Lue tämä tarina suomeksi!

](https://hackernoon.com/lang/fi/kuinka-obsidian-synkronoida-ilmaiseksi%2C-maksullista-suunnitelmaa-ei-vaadita)[UZ

Bu hikoyani o'zbek tilida o'qing!

](https://hackernoon.com/lang/uz/Qanday-qilib-obsidianni-bepul-sinxronlash-kerak%2C-hech-qanday-to'lov-rejasi-talab-qilinmaydi)[LV

Izlasi šo stāstu latviešu valodā!

](https://hackernoon.com/lang/lv/k%C4%81-bez-maksas-veikt-obsidi%C4%81na-sinhroniz%C4%81ciju%2C-nav-nepiecie%C5%A1ams-apmaks%C4%81ts-pl%C4%81ns)

**JA**

## 長すぎる; 読むには

GitHub は、主にソフトウェア開発に使用されるクラウドベースのプラットフォームです。個人のプロジェクトやファイルの管理にも使用できます。Git リポジトリは、すべての編集を追跡しながらメモを保存および同期するのに役立ちます。

![featured image - Obsidian Sync を無料で使う方法! (有料プランは不要)](https://hackernoon.imgix.net/images/0iu1pHRMnqOT3GqhiW0OP3lK20h1-56024i4.png?auto=format&fit=max&w=3840)

[Obsidian は](https://www.youtube.com/watch?v=4zWU4umAMoc&feature=youtu.be&ref=hackernoon.com)、現在入手可能な最高のメモアプリの 1 つです。ローカル ファースト ストレージを備えた強力な Markdown ベースのエクスペリエンスを提供します。ただし、問題が 1 つあります。公式の同期機能は月額約 8 ドルかかります。複数のデバイス間でメモを完全に無料で同期する方法があるとしたらどうでしょうか。このガイドでは、GitHub と Git を使用して、1 円も費やすことなくメモを同期する方法を説明します。

## 必要なもの

やるべきことがたくさんあるように思えるかもしれませんが、心配しないでください。理想的なシナリオでは、約 10 ～ 15 分と次のことだけが必要です。

- GitHub アカウントとリポジトリ
- GitHub アクセストークン
- SSH キー (オプション)
- ギット
- 黒曜石
- Obsidian 用 Git プラグイン
- iPhone用iSHアプリ
- iPhone 用 Obsidian アプリ

## ステップ1: GitHubアカウントとリポジトリを作成する

**GitHub は**、主にソフトウェア開発に使用されるクラウドベースのプラットフォームですが、Obsidian ノートを含む個人のプロジェクトやファイルの管理にも使用できます。

![image](https://miro.medium.com/v2/resize:fit:700/0*0A8BkCmVOjTXfr9z.png)

**Git リポジトリ**(または repo) は、Git が一連のファイルに対するすべての変更を追跡するストレージ スペースです。変更を記録することで、以前のバージョンに戻したり、他のユーザーと共同作業したり、さまざまなデバイス間でファイルを同期したりすることができます。Obsidian のコンテキストでは、Git リポジトリはすべての編集を追跡しながらメモを保存および同期するのに役立ちます。

  

1. [GitHub.com](https://github.com/?ref=hackernoon.com)にアクセスしてサインアップしてください。
2. ログインしたら、 **「新規」**ボタンをクリックして新しいリポジトリを作成します。
3. 名前を付けます（例：「Obsidian-Notes」）。
4. メモが一般公開されないように、リポジトリを必ず**プライベート**に設定してください。
5. **「リポジトリの作成」を**クリックします。

  

![Gitリポジトリ](https://miro.medium.com/v2/resize:fit:700/0*k5QCFLixKc_Q0qcy.png)

Gitリポジトリ

  

## ステップ2: コンピュータにGitをインストールする

Git がインストールされていない場合は、次の手順に従ってください。

- **Windows** : [git-scm.com から Git をダウンロードしてインストールします。](https://git-scm.com/?ref=hackernoon.com)

  

- **Mac** : `brew install git`で Homebrew を使用して Git をインストールします。

  

- **Linux** : `sudo apt-get install git` (Debian ベースのシステムの場合) または sudo dnf install git (Fedora ベースのシステムの場合) を使用します。

  

インストールが完了したら、ターミナル (コマンド プロンプト、PowerShell、または macOS ターミナル) を開き、次のコマンドを実行してインストールを確認します。

```javascript
 git --version
```

### 基本的な Git コマンド

頻繁に使用する 3 つの重要な Git コマンドを次に示します。

```javascript
 git status
```

  

このコマンドはリポジトリの現在の状態を表示します。どのファイルが変更、追加、またはコミット.gitステータスにステージングされたかを示します。

```javascript
 git pull
```

  

このコマンドは、リモート リポジトリ (GitHub) から最新の変更を取得し、ローカル リポジトリを更新します。

```javascript
 git push
```

  

変更を加えたら、git push を使用して GitHub にアップロードする必要があります。このコマンドは、コミットされた変更をローカル リポジトリからリモート リポジトリに送信します。

## ステップ3: GitHubリポジトリをクローンする

それでは、ローカルの Obsidian ボールトを GitHub に接続してみましょう。

- ターミナルを開き、メモを保存するフォルダーに移動します。

  cd C:\Users\rilak\Desktop\notion\github_clone\obsidian_git\backup

- 次のコマンドを実行し、YOUR-REPO-URL を GitHub リポジトリの URL に置き換えます。

```bash
 git clone YOUR-REPO-URL
```

  

- これにより、GitHub リポジトリにリンクされたローカル フォルダーが作成されます。

  

![GitHubリポジトリをクローンする](https://miro.medium.com/v2/resize:fit:700/0*rziDUMO8Pzk6Oi77.png)

GitHubリポジトリをクローンする

  

Obsidian のノートをこのフォルダーに移動して、同期できるようにします。

## ステップ3. GitHubクラシックトークンを取得する方法

GitHub では、Git 操作のパスワードベースの認証が廃止されました。代わりに、より安全な認証方法を提供する**Personal Access Token (PAT)**を使用する必要があります。

![image](https://miro.medium.com/v2/resize:fit:700/0*AyeCBiCMgRvySaUC.png)

GitHubクラシックトークンを取得する方法

**GitHub 開発者設定に移動します:**

- [GitHub トークン設定](https://github.com/settings/tokens?ref=hackernoon.com)を開きます。
- **「新しいトークンの生成」**をクリックし、 **「クラシック」**を選択します。

  

**有効期限と権限の設定:**

- 有効期限を選択するか、**有効期限なし**に設定します (セキュリティ上は推奨されません)。

必要なスコープを選択します。

- repo → プライベートリポジトリにアクセスします。

  

**トークンを生成してコピーします。**

- **「トークンの生成」**をクリックして、**すぐにコピーします**。
- ページを離れた後は、GitHub では再度表示されません。

  

**Git 認証でトークンを使用する:**

- Git 操作で**パスワード**の入力を求められた場合は、代わりにトークンを貼り付けます。

## ステップ 4: 認証用に SSH を設定する (オプション)

同期するたびにパスワードを入力しなくても済むように、SSH 認証を設定できます。

- 次のコマンドを実行して SSH キーを生成します。

```javascript
 ssh-keygen -t ed25519 -C "your-email@example.com"
```

  

- 次を使用して SSH キーをコピーします。

```javascript
 cat ~/.ssh/id_ed25519.pub
```

  

- GitHub にアクセスし、 **「設定」>「SSH および GPG キー」**に移動して、コピーしたキーを追加します。

![認証用の SSH を設定する (オプション)](https://miro.medium.com/v2/resize:fit:700/0*_pFW93ODLKh6KNxO.png)

認証用の SSH を設定する (オプション)

  

これで、システムは GitHub で自動的に認証されるようになります。

## ステップ5: ObsidianでGitプラグインを設定する

Obsidian アプリはすでにお持ちだと思いますので、ここではインストール手順については説明しません。Git プラグインをインストールするための簡単な手順のみを紹介します。

  

Obsidian には Git の同期を容易にするプラグインがあります:

1. Obsidian を開き、 **\[設定\] > \[コミュニティ プラグイン\]**に移動します。
2. 「Git」を検索してインストールします。
3. **自動コミットと同期**を有効にします (間隔を設定します (例: 5 分))。
4. 競合を防ぐために、**起動時にプルを**有効にします。

  

![Obsidian で Git プラグインを設定する](https://miro.medium.com/v2/resize:fit:700/0*869RAQkH7fIjP5Y5.png)

Obsidian で Git プラグインを設定する

  

これで、メモを編集するたびに、Obsidian がメモを GitHub と自動的に同期するようになります。

## ステップ 6: モバイル (iOS、iPhone、iPad) でメモを同期する

モバイルでの同期は少し複雑ですが、それでも実行可能です。

- App Store から**Obsidian**をインストールします。

  

- Linux コマンドを実行できるターミナル アプリ**iSH**をインストールします。

![image](https://miro.medium.com/v2/resize:fit:564/0*LCQ636D2fYnVwax2.png)

- iSHアプリ
- iSH を開き、次のコマンドを使用して Git をインストールします。

```javascript
 apk add git
```

  

- Obsidian ノート用のフォルダーを作成します。

```javascript
 mkdir obsidian
```

  

- マウント コマンドを実行して、Obsidian Vault フォルダーをマウントします。

```javascript
 mount -t ios . obsidian
```

  

- ファイル ピッカーが表示されます。ローカル ボールトがあるフォルダーを選択します。

  

- 次に、次のコマンドを使用します。

  

```javascript
 cd obsidianrm -rf .git clone YOUR-REPO-URL .
```

この手順が完了すると、Obsidian アプリケーションにメモが表示されます。

![オブシディアン iOS](https://miro.medium.com/v2/resize:fit:564/0*QF2250JfX80m4Kzo.png)

オブシディアン iOS

  

## ステップ7: iPhoneにObsidian Gitプラグインをインストールする

チュートリアルの最後のステップ - Git コミュニティ プラグイン。

- Obsidian を開きます。
- \[設定\] > \[コミュニティ プラグイン\] に移動します。
- 「参照」をタップして、Obsidian Git を検索します。
- 「インストール」をタップし、プラグインを有効にします。
- 自動コミット間隔（例：5 分ごと）を設定します。
- Obsidian を開いたときに変更を同期するには、起動時にプルを有効にします。

![Gitプラグイン](https://miro.medium.com/v2/resize:fit:564/0*hbrOXQX8Z2b3ocjl.png)

Gitプラグイン

  

## ビデオチュートリアル

手順に苦労している場合は、詳細なビデオチュートリアルを視聴することをお勧めします。

  

## 結論

設定には少し時間がかかりますが、一度完了するとシームレスに動作します。このガイドが役に立った場合は、コメントでお知らせください。ご質問があればお気軽にどうぞ。

  

乾杯！ ;）

[![Notion](https://hackernoon.imgix.net/images/img-d913jik.jpeg?auto=format&fit=max&w=3840)](https://ntn.so/hn)

  

#### ラベル

[media](https://hackernoon.com/c/media) [#obsidian](https://hackernoon.com/tagged/obsidian) [#github](https://hackernoon.com/tagged/github) [#note-taking-app](https://hackernoon.com/tagged/note-taking-app) [#obsidian-sync](https://hackernoon.com/tagged/obsidian-sync) [#how-to-use-obsidian](https://hackernoon.com/tagged/how-to-use-obsidian) [#obsidian-sync-with-github](https://hackernoon.com/tagged/obsidian-sync-with-github) [#git-repository](https://hackernoon.com/tagged/git-repository) [#hackernoon-top-story](https://hackernoon.com/tagged/hackernoon-top-story)

#### この記事は...

[

Read this story in a terminal

 Terminal

](https://terminal.hackernoon.com/how-to-obsidian-sync-for-free-no-paid-plan-required?ref=hackernoon)[

Read this story w/o Javascript

 Lite

](https://hackernoon.com/lite/how-to-obsidian-sync-for-free-no-paid-plan-required?ref=hackernoon)

![](https://cdn.hackernoon.com/images/ad-assets/ad-pixel-left.png)

X REMOVE AD

[![](https://hackernoon.imgix.net/images/write-ad1.png)](https://hackernoon.com/action-signup?action=10)

![](https://cdn.hackernoon.com/images/ad-assets/ad-pixel-right.png)