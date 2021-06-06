# ACtive Admin
- 管理者画面を実装することができる。
- ユーザーの閲覧画面と管理者画面を分けることで、データの作成、更新、削除を簡単に実行できる。

## インストール

  
```ruby
gem 'activeadmin'
```
### (注) devise と組み合わせて使用する必要があるためインストールしておく
- `devise`のインストール

```ruby
gem 'devise'
```
  
### Active Admin に必要なファイルをインストール

```ruby
rails g devise:install
```
```ruby
rails g activeadmin:install
```
  
## 初期ユーザーデータを登録
- db/seed.rb に初期ユーザデータを作成するためのコードが自動生成されるので下記を実行

```ruby
rails db:seed
```

## モデルを作成
- 管理するモデルを作成
　　
```ruby
rails g model モデル名
```
  
(例)
```ruby
rails g model User name:string age:integer
```
  
- モデルに対する管理画面を作成

```ruby
rails g active_admin:resource モデル名
```
  
(例)
```ruby
rails g active_admin:resource User
```
  
## 管理画面でデータを更新する設定
- 管理するモデルのデータを更新するために、更新したいカラムを`app/admin/users.rb`に設定

```ruby
ActiveAdmin.register User do
  permit_params :カラム名
end
```
  
(例)
```ruby
ActiveAdmin.register User do
  permit_params :name, :age
end
```
  
## 管理者画面のみにスタイルを設定
- デフォルトでは、他のビューファイルにも ActiveAdmin のスタイルが反映されてしまうので ActiveAdmin で使用されている css と js を vendor ディレクトリに移動
  
- ディレクトリを作成
  
```ruby
mkdir -p vendor/assets/javascripts
mkdir vendor/assets/stylesheets
```
  
- 作成したディレクトリに移動
  
```ruby
mv app/assets/javascripts/active_admin.js vendor/assets/javascri
pts/active_admin.js
mv app/assets/stylesheets/active_admin.scss vendor/assets/stylesheets/active_admin.scss
```
  
## 管理者の通常ログイン制限をパス
- `devise`の機能で`app/controllers/application_controller.rb `に`before_action :authenticate_user! `
を使用している場合は管理者も通常ログイン必須となってしまうため、管理者ログインのみとするために`config/initializers/active_admin.rb`下記を追記
  
(注)`before_action :authenticate_user!`を設定している時のみ
```ruby
ActiviAdmin.setup do |config|
  config.skip_before_action :authenticate_user!
end
```
  
  
