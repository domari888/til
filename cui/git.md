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
  
- コンフリクトが発生した場合に merge を取り消す
```
git merge --abort
```

<br>

## git rebase -i
```
git rebase -i コミットID
```
### コミットをまとめる
コミット履歴を確認する
```
> git log --oneline
71b7852 (HEAD -> feature/sample) コミット５
148bc5c コミット4
a6ffbed コミット3
b58437d コミット2
ec871c0 コミット1
```
  
まとめたいコミットの1つ手前の`コミットID`を指定する
  
- (例)`コミット2`にまとめたい場合
```
git rebase -i ec871c0
```
  
表示される vim でまとめたいコミットの次にまとめるコミットを移動して`pick`を`f`に変更する
  
- (例)`コミット５`を`コミット２`にまとめる場合
  
【変更前】
```
pick b58437d コミット2
pick a6ffbed コミット3
pick 148bc5c コミット4
pick 71b7852 コミット５
```
【変更後】
```
pick b58437d コミット2
f 71b7852 コミット５
pick a6ffbed コミット3
pick 148bc5c コミット4
```

<br>

## git branch
  
### ローカルブランチ名を変更する
```
git branch -m 変更前のブランチ 変更後のブランチ
```
  
### リモートブランチ名を変更する
1. ローカルブランチ名を変更
  
2. 古い名前のブランチを削除
```
git push --delete origin 古いブランチ
```
3. 新しい名前のブランチを追加
```
git push origin 新しいブランチ
```

## git diff
### git diff ブランチ名 ブランチ名
ブランチ同士の差分を比較

(例)`develop`と`feature/hoge`の差分を比較
```
git diff develop feature/hoge
```
