# SSH Keyの作成
次のコマンドで作成する。
```ruby:qiita.rb
 % ssh-keygen -t rsa -b 4096 -C <email_address>
```
-tでおそらく暗号化方式を選択している。  
-bは不明。  
-Cでgithub accout と同じメアドを入力する。  
すると、次のようなテキストが現れるので、任意の名前を鍵につける。ここで、HOMEにはユーザー名が表示される。
```ruby:qiita.rb
Enter file in which to save the key (/Users/HOME/.ssh/id_rsa): <key_name>
```
その後、パスワードの入力と確認が求められるが、空白でも良い。  
その後、次のコマンドを打ち込み、鍵が正しく生成されていることを確認する。
```ruby:qiita.rb
 % ls | grep <key_name>
 # <key_name>
 # <key_name>.pub
```
実行すると上のような二つの出力が得られる。.pubとはpublicの略であり、公開鍵のことである。従って、何も書いていない方は秘密鍵である。これは絶対に公開してはいけない。  
次に公開鍵を次のコマンドで取得する。
```ruby:qiita
 % cat <key_name>.pub
```
実行すると公開鍵が表示される。ターミナルに表示された文字列をコピーするには文字をハイライトするだけで良い。なぜならターミナルによってCtrl＋Cには異なる役割が与えられていることがあるからである。  
また、コマンドラインのみを用いてコピーすることもできる。
```ruby:qiita
 % pbcopy < ~/<key_name>.pub
```
