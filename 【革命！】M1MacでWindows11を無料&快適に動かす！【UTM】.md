# 【革命！】M1MacでWindows11を無料&快適に動かす！【UTM】

[https://zenn.dev/teba_eleven/articles/aedc265d30e751](https://zenn.dev/teba_eleven/articles/aedc265d30e751)

![](https://storage.googleapis.com/zenn-user-upload/topics/e221d43143.png)

![](https://storage.googleapis.com/zenn-user-upload/topics/674a1a02b9.png)

# はじめに

![](https://storage.googleapis.com/zenn-user-upload/d682c377be7c-20220915.png)

今回は、M1MacでWindows11を快適に動かすことに成功したので、

- やり方
- 動くアプリなどの検証

などを紹介していきます！

とても難しいこともせず、インストールなどに時間はそこまでかからなかったのでかなりオススメです。

# モチベーション

ちゃんみお.py

```
if price == "Paid" and platform　== "M1Mac":
	print("ノーサンキューだよ!!!")
elif price == "Free" and platform　== "intelMac":
	print("みそスープ")

```

WindowsをM1Macで動かす有名なアプリとして、「Parallels® Desktop」というものがありますが、なにせ

- 無料でずっと使えない
- ライセンスが高い

などがあるので、どうにかしてWindowsをM1かつ無料で動かしたいというモチベーションです。

## 著者について

普段はScratchという言語で[ニューラルネットワーク](https://www.chickensblog.com/scratch-neural-network-no-library/)を作ってたり、それをブログとかにまとめたり、自分が遭遇した[エラー](https://zenn.dev/teba_eleven/articles/c0649d0195ba74)やバグなどの解決方法をシェアしてます。

こどもたちに無料でプログラミングを教える「CoderDojo」やってますので、よければ遊びに来てください！

### ブログ

[https://embed.zenn.studio/card#zenn-embedded__95497ab020b2b](https://embed.zenn.studio/card#zenn-embedded__95497ab020b2b)

### イベント

[https://embed.zenn.studio/card#zenn-embedded__e225d4dce2029](https://embed.zenn.studio/card#zenn-embedded__e225d4dce2029)

**この投稿へのコメント、いいね、自作ブログサイトの閲覧してもらえるととても励みになります！**

# 著者の環境

- M1MacBookAir
- RAM:8GB
- SSD:256GB

最小構成でも意外とサクサク動いてくれているので大丈夫だと思います。

# M1Mac上で動かす手順

[https://embed.zenn.studio/card#zenn-embedded__810a8feccc341](https://embed.zenn.studio/card#zenn-embedded__810a8feccc341)

上記のリンク先で実際の動かし方を解説しています。

使っている技術は

- homebrew
- UTM

ぐらいです。

## homebrewについて

パッケージを管理してくれます。今回はUTMやそれに必要なものをインストールするために使います。管理がしやすいのでhomebrewを選びました。

## UTMについて

仮想マシンです。これを使って実際にWindows11をM1Mac上で動かしています。

# M1で動かすWin11の性能

![](https://storage.googleapis.com/zenn-user-upload/884b72a41718-20220915.png)

- インターネット問題なし
- 音声問題なし
- アプリ動作問題なし

普通のWin機として十分に使える感じです。

# 有名アプリの動作検証

## ✅Chrome

![](https://storage.googleapis.com/zenn-user-upload/bcf8e285110c-20220917.png)

👍

## ✅Aviutl

![](https://storage.googleapis.com/zenn-user-upload/6cf99bca4f18-20220917.png)

動いたー！！

! 余談ですが、Aviutlのタイムラインって最初から入っているのかと思ったら、拡張機能として追加しないといけなかったの忘れてました😅

## ✅ゆっくりムービーメイカー(YMM4)

![](https://storage.googleapis.com/zenn-user-upload/7a83e94a1c6d-20220917.png)

しゃべっったあああーーー！！

! あれ？なんか音が聞こえない…と思ってヘッドホンの端子を抜いたら音が聞こえてきました

※画像表示とかも普通にいけました

## ✅ミクミクダンス(MMD)

![](https://storage.googleapis.com/zenn-user-upload/19aed72c6ff8-20220917.png)

そのままではエラーがでたのでC++、DirectXとか入れておきました。

![](https://storage.googleapis.com/zenn-user-upload/b73f11874442-20220917.png)

動いたー！！

結構サクサク動くし、これも問題なさそう。

![](https://storage.googleapis.com/zenn-user-upload/5b74513da8ca-20220917.png)

*ぐりぐりできる*

## ✅統合版マインクラフト

![](https://storage.googleapis.com/zenn-user-upload/0df262fb9dbc-20220918.png)

流石に3D描画なので重たいですが、統合版マインクラフトは動きました。ただし、windows版マインクラフトのみをmicrosoftstoreから持ってこないと起動できない…

! そもそもマイクロソフトストアが入っていないので海外の情報を頼りに探しまくった結果、x86の物を入れることによって解決。ログインに必要なアプリがインストールできるようになったので、オンラインプレイも可能になった。

※2022/09/18検証

## 🆘チートエンジン

![](https://storage.googleapis.com/zenn-user-upload/cb05f8246b3a-20220918.png)

スピードハックやメモリも検出できなかった。自分はアーキテクチャなどのローエンドを詳しく知らないのだけど、この環境に対応しているバージョンもあるのかもしれない。

# まとめ

- M1MacでもWindows11を動かせた
- AviutlやYMM4など、有名なアプリなどは全く問題なく動いた
- 普通に使えるほどサクサク動いた

# 関連記事

# 追記

他に何が動くか知りたい方はコメントなどで教えてください。

[[【M1】UTMを使ってM1Mac上でWindows11を動かす手順   チキンズブログ！]]

[[【M1】UTMを使ってM1Mac上でWindows11を動かす手順   チキンズブログ！]]