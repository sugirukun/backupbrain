# 【Notion】Google Drive上のファイルをNotionに取り込む #GoogleDrive - Qiita

カテゴリー: Notion, Qiita Zenn note, アプリ, 情報技術
作成日: 2025/02/27
URL: https://qiita.com/C_HERO/items/7ac1e67409e40ed2cd35

NotionにGoogle Drive上のファイルを取り込む方法（の覚え書き）です。

## 方法

NotionにGoogle Drive上のファイルを取り込む方法は以下の通り。

### 1. インポート

一度、Google Drive上から対象のファイルをDLして、インポートする。

「個別インポート」と「一括インポート」の2種類がある。

### 2. インテグレーション

Google Drive上のファイルにアクセスする。

「リンクを埋め込む」と「Google Driveを閲覧」の2種類がある。

※取り込むというよりは、参照 or 埋め込む イメージ。

## 手順

ほぼほぼNotionの公式リファレンスの通りですが、、それぞれの手順を以下に載せておきます。

### 1. インポート

### (1) 個別インポート

まずは個別インポートについて。

その名の通り、1ファイルずつ個別でインポートする方法です。

①Google Driveにアクセスし、対象ファイルの右端の「その他の操作」（①）>「ダウンロード」（②）をクリックしてローカル環境にDLする。

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F356958%2F1401c407-06c3-8929-f04b-65b0be409b95.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=5c8d2d6eb9e66a27e05323572e7acd0e)

②Notionの対象ワークスペースを開き、サイドバーの「インポート」をクリック。

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F356958%2F3b789aad-d672-af7d-3bc4-b7049467d1bf.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=53b09f9bc10def4d7dc24c0d46d00290)

③「データをインポート」が開いたら、「Word」をクリックし、①でDLしたファイルを選択。

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F356958%2F43535e12-0bde-ad6b-5351-925f6d37d215.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=1b8e8a7ec9dcfb232aee4f83834b8d05)

④ファイルがアップロード → インポート されます。

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F356958%2F12a0df5f-f296-ce3d-f16f-411df91548b5.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=43282fb03df3f34b35a7eb18d9d486b4)

⑤プライベート直下に対象ファイルがインポートされ、開かれた状態になれば完了！

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F356958%2Fc76ddf68-a013-b5ca-17d3-87a08dc63132.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=223cdf706fbe8126514a2699ac2286ff)

Google Docs → Wordに変換されたファイルは、「Word」の他、「Google Docs」、「CSV」、「テキストとマークダウン」でもインポート可能でした。

Google Sheets → Excelに変換されたファイルは、「CSV」、「テキストとマークダウン」でインポートできました。1シート目しかインポートされないので、その点にはご留意を。

Google Slides → powerpointに変換されたファイル、および画像ファイルは、そのままだとインポート不可のため、(2)一括インポートで取り込みます。Word、Excel形式のファイルと違い、添付ファイルとして取り込まれる点、ご留意を。

### (2) 一括インポート

続いて、一括インポートについて。

対象のファイル一式をZIPファイルで取り込みます。

①Google Driveにアクセスし、対象フォルダの右端の「その他の操作」（①）>「ダウンロード」（②）をクリックしてローカル環境にDLする。

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F356958%2F7c76b963-cf05-b63b-1647-70dd309341b0.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=caa2f6473ae8aadc4ff579c78665fc85)

公式リファレンスには、Googleデータエクスポートを使うよう記載がありますが、この方法でもいけました。メール受信を待つ時間がない分、スピーディー。

なお、今回DLしたフォルダの構造は以下の通り。

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F356958%2F1cb1c86f-0f9f-c06d-f831-fc2024803bb4.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=e176df12cb29be3bec647b87edeaacce)

②対象フォルダをまるっと圧縮したZIPファイルがDLされます。

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F356958%2Fe16d52f4-b8cd-2731-556e-55abc919082a.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=d058d32a0d4ccea1ec4d09bd7a67e5f1)

③Notionの対象ワークスペースを開き、サイドバーの「インポート」をクリック。

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F356958%2F9469c972-67cd-5c0f-b232-0ebf63a4f8db.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=c56b4b7e910a070e4aaf1bbc5787ac68)

④「データをインポート」が開いたら、「汎用インポート」をクリックし、①でDLしたZIPファイルを選択。

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F356958%2F49605ccf-149a-8827-1321-499969988724.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=4c7077070562842220661f6de04e0917)

⑤インポート後の様子です。「{ZIPファイル名}インポート（YYYY年MM月DD日）」のタイトルでページが作成され、配下にGoogle Docs、Spreadsheet（DL後はWord、Excel）由来のページが作成され、Google Slide（DL後はPowerPoint）、画像ファイルは添付ファイルとして、アタッチされています。

![](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F356958%2Fff292669-c683-a689-302d-dd3d2f8a183c.png?ixlib=rb-4.0.0&auto=format&gif-q=60&q=75&s=d7136371de3acf3d97c874903d2087aa)

フォルダ構造は保持されないようです。Google Drive上ではサブフォルダ配下にあった、サンプル⑦、サンプル⑧.pngが他ファイルと同階層に来てしまいました、、

### (3) インポートまとめ

各ファイルのインポートに関して、表にまとめました。

| ファイルの種類 | 個別インポート | 一括インポート | 一括インポートでの挙動 | 備考 |
| --- | --- | --- | --- | --- |
| Google Docs（Word） | Word, Google Docs, CSV, テキストとマークダウン | 汎用インポートからZIP形式で取り込み | サブページが作成される | 一括インポートの場合、フォルダ構造は保持されない（以降同様） |
| Google Sheets（Excel） | CSV, テキストとマークダウン | 同上 | 同上 | インポート対象は1シート目のみ |
| Google Slides（PowerPoint） | 不可 | 同上 | 親ページに添付される |  |
| PDFファイル | 不可 | 同上 | 同上 |  |
| 画像ファイル | 不可 | 同上 | 同上 |  |

### 2. インテグレーション

インテグレーションにも、2種類の方法があります。

### (1) リンクを埋め込む

まずは、「リンクを埋め込む」方法から。

①Google Drive上のNotionから参照させたいファイルに関し、「その他の操作」（①） > 「共有」（②） > 「リンクをコピー」をクリックし、対象ファイルへのリンクを取得します（③）。

②Google Drive上の資料を参照したいページにて、「/google」と打ち込み（①）、「Google Drive」を選択（②）。

③表示されるテキストボックスに①でコピーたリンクをペーストし（①）、「リンク」をクリック（②）

④対象ファイルの内容が埋め込まれたら完了です！

### (2) Google Driveを閲覧

続いて、「Google Driveを閲覧」について。

①Google Drive上の資料を参照したいページにて、「/google」と打ち込み（①）、「Google Drive」を選択（②）。

②「Google Driveを閲覧」をクリックし（①）、対象のGoogleアカウントを選択（②）。

Googleアカウントの連携がまだの場合、もしくは別のアカウントを参照したい場合は、「別のアカウントを接続」より、対象のアカウントに接続してください。

③ファイル一覧が表示されるので、埋め込みたいファイルを選択します。

④対象ファイルの内容が埋め込まれたら完了！

最終的に対象ファイルがページに埋め込まれるという点で、「(1) リンクを埋め込む」と何ら変わりはありません。

お好みのほうを使うとよいでしょう。

## 使い分けについて

インポートとインテグレーションの使い分けについて、考えてみました。

### インポート

- Google Drive → Notionに移行したい場合

### インテグレーション

- 当面はGoogle Driveメインで使いたい場合
- Google Drive上にある他社や他チームの共有ファイルを参照したい場合

といったところでしょうか。

場合によって使い分けるのがよさそうですね。

## 終わりに

一括インポートについて、英語ページ含め、いちばん最後の文が

> 
> 
> 
> Word を選択し、.docxファイルをアップロードします。
> 

となっているのですが（2023年10月9日現在）、おそらく

> 
> 
> 
> 汎用インポート を選択し、ZIPファイルをアップロードします。
> 

なんじゃないかなぁと。。

最初、1ファイルずつしか取り込みしかできない・・?? と焦ってしまいました・・。

フォルダ構造が多階層になっている場合、工夫が必要ですが、一括インポートができれば、Google Drive → Notionへの移行はある程度スムーズにできそうですね。

## 参考

- [データのインポート | [[import data into]]
- [Google Driveインテグレーション | [[]]