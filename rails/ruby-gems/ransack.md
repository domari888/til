# Ransack
  
検索機能

<br>

## モデルのカラムを検索する
コントローラに`ransack`を用いた検索機能を利用するための処理を記載
(例)`Post`モデルの`content`を検索する
```rb
class PostsController < ApplicationController

  def index
    @q = Post.ransack(params[:q])
    @posts = @q.result
  end
end
```
```rb
<%= search_form_for @q do |form| %>
  <div class="form-group pb-3">
    <%= form.label :content_cont, "キーワード" %>
    <%= form.search_field :content_cont, class: 'form-control' %>
    <%= f.submit "検索" %>
  </div>
<% end %>
```

<br>

## 関連するモデルを検索する
```
<%= search_form_for @q do |f| %>
  <%= f.フォームヘルパー :関連するモデルの名前_関連するモデルのカラムの名前_述語 %>
  <%= f.submit "検索" %>
<% end %>
```
  
### 一対多
(例)`Post`モデルに紐づく`User`モデルの`name`を検索する
```rb
<%= search_form_for @q do |form| %>
  <div class="form-group pb-3">
    <%= form.label :user_name_cont, "キーワード" %>
    <%= form.search_field :user_name_cont, class: 'form-control' %>
    <%= f.submit "検索" %>
  </div>
<% end %>
```
- 関連するモデルの名前  `user`
- 関連するモデルのカラムの名前  `name`
- 述語  `cont`
  
### 多対多の場合
(例)`Post`モデルに紐づく`Tag`モデルの`name`を検索する
```rb
<%= search_form_for @q do |form| %>
  <div class="form-group pb-3">
    <%= form.label :tags_name_cont, "キーワード" %>
    <%= form.search_field :tags_name_cont, class: 'form-control' %>
  </div>
<% end %>
```
(注)`関連するモデルの名前`は複数形にする
- 関連するモデルの名前  `tags`
- 関連するモデルのカラムの名前  `name`
- 述語  `cont`

<br>

## 関連するモデルを調べる

【rails c】
```
> rails c
Running via Spring preloader in process 21757
Loading development environment in sandbox (Rails 6.1.4)
Any modifications you make will be rolled back on exit
irb(main):001:0> Post.ransackable_associations
  => 関連するモデルが表示される
```
