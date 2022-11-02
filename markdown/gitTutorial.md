# Git
参考記事：  
よく使うGitコマンド19選！  
https://www.sejuku.net/blog/5816  
## gitとは
Gitとは、バージョン管理ソフトウェアである。  
バージョン管理ソフトウェアとは、ドキュメントやプログラム、ウェブサイトなどの変更を管理するものである。

次のコマンドで隠しファイル(.gitconfig)などを表示できる。
```ruby:qiita.rb
 % ls -la
```
ファイルの状態を確認するには、次のコマンドを用いる。
```ruby:qiita.rb
 % git status
```
編集された場合、modified、まだ追跡していない場合untrackedと表示される。  
追跡されていないデータを追跡するには、次のコマンド
を用いる。
```ruby:qiita.rb
 % git add <file_name>
```
<file_name>で個別に指定することもできるが、通常は.
と入力し、現在追跡されていない全てのファイルを追跡することが多い。  
次に、変更をコミット（ローカルに保存）するには次のコマンドを用いる。
```ruby:qiita.rb
 % git commit -m "commit message"
```
-mというオプションを用いることでコミットメッセージを編集できる。また、-mは何度でも用いることができる。  
最後に、変更をオンライン上のリポジトリに反映するには次のコマンドを用いる。
```ruby:qiita.rb
  % git push
```

## gitを使っていて詰まった点
### .DS_Storeが自動生成される
これはMac特有の現象らしいのですが、Macではフォルダやファイルに関するメタ情報がを保存する.DS_Storeという隠しファイルが自動で作成されます。通常の使用方法では邪魔にならないのですが、
```
git status
```
と打つと常に出てきて、ブランチのチェックアウトもできないので邪魔で仕方ないです。そこで、次のコマンドで.DS_Storeを削除します。  
まずは、すでにコミットされている.DS_Storeを削除します。
```
  find . -name .DS_Store -print0 | xargs -0 git rm -f --ignore-unmatch
```
次に、.gitigonreに.DS_Storeを追加し今後コミットしないようにします。
```
echo .DS_Store >> .gitignore
```
その後この変更をコミットします。
```
git add .gitignore
git commit -m 'Remove all .DS_Store'
```
  
参考記事：  
.DS_Storeをリポジトリから削除しコミットしなくする  
https://it-engineer.hateblo.jp/entry/2018/12/21/091741  
.DS_Storeファイルとは？  
https://aprico-media.com/posts/3943  

## 新しく作ったブランチをpushできない
ブランチを次のようなコマンドで作成した。
```
  git branch <branch_name>
```
その後、次のコマンドでブランチをチェックアウトした。
```
  git checkout <branhc_name>
```
変更を加えたあと次のコマンドで変更をコミットした。
```
  git add .
  git commit -m "commit_mesage"
```
そして、これをリモートリポジトリにpushするために次のコマンドを実行したらところエラーを吐いた。
```
  git push
  <!-- fatal: The current branch aoba has no upstream branch.
  To push the current branch and set the remote as upstream, use  

      git push --set-upstream origin aoba -->
```
どうやら、upstream branchというリモートようのブランチがなかったためにエラーが生じたようなので、言われた通りコマンドを実行した。
```
      git push --set-upstream origin aoba -->
```
問題なく実行され、最後にpushを行った。
```
  git push
```
問題なくpushできた。
