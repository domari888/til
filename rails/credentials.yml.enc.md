# credentials.yml.enc
  
公開鍵。  
秘密鍵（`master.key`）を使用して開示することができる。  
`rails new`コマンドで Rails アプリを作成した人が秘密鍵(`master.key`)を所有している。
**(注)秘密鍵(master.key)は公開してはいけない**
  
## credentials.yml の編集
### VScode で開く
```
EDITOR='code --wait' rails credentials:edit
```
  
### Vim で開く
```
EDITOR=`vi` rails credentials:edit
```
  
<br>

## アプリパスワードの作成
(例)　`Google`のアプリパスワード、メールアドレスを作成
```
gmail:
  address: メールアドレス
  password: アプリパスワード
```
作成後下記が表示される
```
New credentials encrypted and saved.
```
