## git clone リポジトリのURL
  
## git push origin HEAD
- 現在のブランチのローカルリポジトリの内容をリモートリポジトリに反映させる
  
## git fetch
   
- リモートリポジトリのブランチを origin/ブランチ名 としてローカルリポジトリに取り込む
- ワークツリーには反映されない
  
## git fetch origin master
  
- リモートリポジトリのmasterブランチを origin/master ブランチとしてローカルリポジトリに取り込む

## git fetch --prune
  
- fetchするついでにGitHubから削除されたブランチを削除

## git merge ブランチ名
  
- 指定したブランチの変更を現在のブランチに統合
  
(例)`master`ブランチを現在のブランチに統合
```
git merge origin/master
```
