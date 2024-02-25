# Homebrew でのインストール手順
## Nodebrew インストール
``` 
brew install nodebrew
```
### バージョン確認
``` 
nodebrew -v
```

<br>

## PATH を通す
### シェルを確認
```
echo $SHELL
```
- zshを利用している場合
`/bin/zsh`
- bashを利用している場合
`/bin/bash`

### PATH を設定
- zshを利用している場合
```
echo 'export PATH=$HOME/.nodebrew/current/bin:$PATH' >> ~/.zshrc
```

<br>

## Node.js インストール
### バージョンリスト確認
```
nodebrew ls-remote
```
### バージョン指定
```
nodebrew install -binary バージョン番号
```
### 最新バージョン
```
nodebrew install -binary latest
```
### 安定バージョン
```
nodebrew install-binary stable
```
### バージョン確認
```
nodebrew ls

　# インストールされているバージョンのリスト
v14.15.3

# 現在バージョン(インストール時は none)
current: none
```
### 参考
[macOS に Node.js をインストールする手順 (nodebrew編)](https://ensei1375.com/nodejs-install/)
  
[Node.jsの環境構築](https://zenn.dev/mk13182008/articles/42ce264f3f2b38)
  
[【Mac用】nodebrewを使ってNode.jsをインストールする方法](https://ensei1375.com/nodejs-install/#google_vignette)
