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
  
### Comment モデルを作成する場合
Active Admin では管理者側で扱う Comment モデルが存在するため、競合してエラーが起きてしまう。
  
(解決策)
`config/initializers/active_admin.rb`で下記の記述のコメントアウトを外し、管理者側で扱う Comment モデルを`AdminComment`モデルとして扱う
```rb
config.comments_registration_name = 'AdminComment'
```
  
<br>
  
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
  
<br>
  
## アクションを追加
(例)`Post モデル`の詳細ページに`アプリへの投稿詳細リンク`を作成
```rb
action_item :show_page, only: :show do
  link_to 'アプリで見る', post_path(post)
end
```
  
<br>
  
## アクションごとのカスタマイズ
### 画像を表示
(例)詳細画面で画像を表示
- `style`を設定して画像サイズを設定
```rb
show do
  attributes_table do
    row :avatar do
      image_tag(user.avatar.url, :style => 'height:100px;')
    end
  end
end
```
  
### チェックボックスをオンにする
- `terms_of_use`カラムのチェックボックスをオンにする
```rb
form do |f|
  f.inputs do
    f.input :terms_of_use, input_html: { value: '1' }
  end
end
```
  
<br>
  
## 作成時(new)のみフォームを表示する
```rb
if form.object.new_record?
  # フォーム
end
```
(例)新しいレコードでなければ保存されている画像を表示する
```rb
<%= form_with model: [:admin, resource], local: true do |form| %>
  <% unless form.object.new_record? %>
    <%= form.label '現在の画像' %>
    <%= form.collection_check_boxes :photo_ids, resource.photos, :id, :image, checked: false, include_hidden: false do |f| %>
      <%= f.check_box %>
      <%= image_tag(f.object.image.url, size: '100x100') %>
    <% end %>
    <p class="inline-hints">削除する場合はチェックを入れてください</p>
  <% end %>
<% end %>
```

<br>

## フォームをパーシャルで分割して作成する
`form partial: '○○○'`とすることで指定したテンプレートファイルを返す。

(例)`app/views/admin/users/_form.html.arb`(テンプレートファイル)を返す
```rb
# app/admin/users.rb

ActiveAdmin.register User do
  form partial: 'form'
end
```
(例)`form_with`を使用したテンプレートファイル
```rb
# app/views/admin/users/_form.html.arb

<%= form_with model: [:admin, resource], local: true do |form| %>
  <fieldset class="inputs">
    <ol>
      <li>
        <%= form.label :email %>
        <%= form.email_field :email, required: true %>
      </li>
    </ol>
  </fieldset>
<% end %>
```
  
参考文庫 :
  
[Customizing the Form - Active Admin](https://activeadmin.info/5-forms.html#:~:text=Cancel%27%20buttons%0Aend-,Partials,%7C%0A%20%20%20%20%20%20%2D%20t.input%20%3Atag%0A%20%20%20%20%3D%20f.actions,-Nested%20Resources)
  
[ActiveAdminでモデルの管理画面を.erbでカスタマイズして作る](https://qiita.com/roba4coding/items/c27d3635c152b3a868f3#%E6%96%B0%E8%A6%8F%E7%B7%A8%E9%9B%86%E7%94%BB%E9%9D%A2%E3%83%95%E3%82%A9%E3%83%BC%E3%83%A0%E7%94%BB%E9%9D%A2)

<br>

## 一覧ページ(index)でソート順を定義する
(例)`id`を昇順で表示する
```rb
ActiveAdmin.register Post do
  config.sort_order = 'id_asc'
end
```
参考文庫 :
[Customizing the Index Page - Active Admin](https://activeadmin.info/3-index-pages.html#:~:text=Index%20default%20sort%20order)

<br>

## デフォルトの詳細ページ(show)データを表示する
`default_main_content`を記述することでデフォルトのデータを表示する
  
(例)デフォルトのデータの他に文字列を追加
```rb
show do
  div do
    '追加する文字列を表示'
  end
  default_main_content
end
```
参考文庫 :
[Customize the Show Page - Active Admin](https://activeadmin.info/6-show-pages.html#:~:text=If%20you%20want%20to,charts%27%0A%20%20end%0A%20%20default_main_content%0Aend)
