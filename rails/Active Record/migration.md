## マイグレーション
### マイグレーションを作成
- モデルを生成
  - モデルのジェネレータとscaffoldジェネレータは、新しいモデルを追加するマイグレーションを生成する
```
rails g model モデル名 カラム名:データ型
```
(例) `users`テーブルに、カラム名が`name` ,データ型が`string`のカラムを持つ `User`モデルを生成
  
```
rails g model User name:string
```
  
(例) `uniq`をつけることで一意制をつけることができる

```
rails g model User name:string email:string:uniq
```

### マイグレーションを確認

```
rails db:migrate:status
```
- `rails db:migrate`を実行済みの場合は `up`, 実行前の場合は `down`
  
(例) 
```
database: devise_admin_sample_development

 Status   Migration ID    Migration Name
--------------------------------------------------
   up     20210614042403  Devise create admin users
  down    20210614115519  Create notifications
```
  
### ロールバック
- 直前に行ったマイグレーションをロールバックする
  - ロールバックすることで `up` が `down` になる

```
rails db:rollback
```
  
- 複数ロールバック行う場合は `step` パラメータを指定する
  - (例)　直前に行った３つのマイグレーションをロールバックする

```
rails db:rollback STEP=3
```

- ロールバックを行うマイグレーションを指定
  - (例) Migration ID 20210614115519 を指定
  
```
rails db:migrate:down VERSION=20210614115519
```
  
- migrate されていないファイルを確認
```
rails db:abort_if_pending_migrations
```
  
<br>

## マイグレーションファイルの削除
  
- 削除したいマイグレーションファイルの`Migration ID`を指定して`down`にする
```
rails db:migrate:down VERSION=`Migration ID`
```
- マイグレーションファイルを削除
```
rm -rf db/migrate/`Migration ID`
```
  
<br>
  
## マイグレーションファイル名の変更
  
削除したいマイグレーションファイルの`Migration ID`を指定して`down`にする  
```
rails db:migrate:down VERSION=`Migration ID`
```
ファイル名を変更後、マイグレーションを実行
```
rails db:migrate
```
