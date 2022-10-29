# Macを使っていて詰まったところ
最新版のMac OSにアップデートしたときにgitのインストールを要求されたので
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
色々エラーがでて同じエラーも出たのでとりあえずXcodeのディベロッパーツールをインストールすることにした。
```ruby:qiita
 xcode-select --install
```
それなりに時間がかかるので電源に接続してスリープしておくことを推奨する。インストール画面がどのウィンドウにも出てきて作業がものすごくやりづらいのでスマホでも触っていた方が効率的。  
もう一度`brew doctor`を実行し、エラーが解消されているか確認した。インストールしたディベロッパーツールのアップデートを要求されたので次のコマンドを実行した。
```ruby:qiita
 softwareupdate --all --install --force
```
しかし、アップデートは検出されなかった。
