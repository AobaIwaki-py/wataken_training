参考記事：https://codelikes.com/github-ssh-connection/
# SSH Keyの作成
次のコマンドで作成する。
```ruby:qiita.rb
 % ssh-keygen -t rsa -b 4096 -C <email_address>
```
-tでおそらく暗号化方式を選択している。  
-bは生成するsshのbit数を指定している。
-Cでgithub accout と同じメアドを入力する。  
すると、次のようなテキストが現れる。デフォルトでは<>内のフォルダに保存される。初めてならこちらを推奨。名前をつけることで好きな場所に好きな名前で保存できる。
```ruby:qiita.rb
Enter file in which to save the key (/Users/HOME/.ssh/id_rsa): ~/<key_name>
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
 % cat ~/<key_name>.pub
```
実行すると公開鍵が表示される。ターミナルに表示された文字列をコピーするには文字をハイライトするだけで良い。なぜならターミナルによってCtrl＋Cには異なる役割が与えられていることがあるからである。  
また、コマンドラインのみを用いてコピーすることもできる。
```ruby:qiita
 % pbcopy < ~/<key_name>.pub
```
macOS Sierra10.12.2以降の場合（おそらくほぼ全て）次の操作を行い、configを編集する。
```ruby:qitta
 % eval "$(ssh-agent -s)"
 # Agent pid 59566
 % vim ~.ssh/config
 # 以下vim内部
 - Host *
 -   AddKeysToAgent yes
 -   UseKeychain yes
 -   IdenrityFile ~/.ssh/id_rsa
 # vimから出る
 % ssh-add -K ~/.ssh/id_rsa
#  WARNING: The -K and -A flags are deprecated and have been replaced
#          by the --apple-use-keychain and --apple-load-keychain
#          flags, respectively.  To suppress this warning, set the
#          environment variable APPLE_SSH_ADD_BEHAVIOR as described in
#          the ssh-add(1) manual page.
```
最後のコマンドで変更を保存する。-Kに関して警告が出るが実行はされる。警告を回避するには、-Kを--apple-use-keychainに変更すればよい。