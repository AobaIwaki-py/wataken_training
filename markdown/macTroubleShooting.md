# Macを使っていて詰まったとこ
## MacOsVentura13.0アップデートしたときに今まで問題なく動いていたのにgitのインストールを要求された
```ruby:qiita
 brew install git
#  Warning: No developer tools installed
#  Install the Commmand Line Tools:
#  xcode-select --install
```
のようなエラーをはいたのでとりあえずそれ以外に困ったことはないか次のコマンドを実行した
参考ページ：
https://qiita.com/noraworld/items/ce90783994ce2607a5ca
```ruby:qiita
 brew docter
```
色々エラーがでてたのでとりあえず一番上に出てきたコマンドを実行した。
```ruby:qiita
 xcode-select --install
```
それなりに時間がかかるので電源に接続してスリープしておくことを推奨する。インストール画面がどのウィンドウにも出てきて作業がものすごくやりづらいのでスマホでも触っていた方が効率的。  
もう一度`brew doctor`を実行し、エラーが解消されているか確認した。インストールしたディベロッパーツールのアップデートを要求されたので次のコマンドを実行した。
```ruby:qiita
 softwareupdate --all --install --force
```
しかし、アップデートは検出されなかった。3回ほどインストールとアンインストールを繰り返して色々と試行錯誤をしてもエラーが出てくるのでパソコンに詳しい友人に聞いたところ`brew doctor`は割と厳しめにWarningが出るのでWarning程度だったら無視していいとのことだった。とりあえずは放置しておくことにする。
## 三本指でドラッグしたいのに設定画面にない(Mac OS Ventura13.0)
研究室のMac TipsというWikiに三本指でドラッグできるように設定を変えたほうがいいとあったのに設定画面のどこを探してもポインタコントロールという項目を見つけられなかった。色々調べた挙句アクセシビリティの中にポインタコントロールがあることが発覚し、無事設定することができた。