# form_with
[参考](https://pikawaka.com/rails/form_with)
  
## local: false
非同期通信でフォームを送信する
  
```rb
<%= form_with model: @post, local: false do |form| %>
  ~ 省略 ~
<% end %>
```

<br>

## model: [ ]
複数のインスタンス変数を渡す
  
```rb
<%= form_with model: [@post, @comment] do |form| %>
  ~ 省略 ~
<% end %>
```

<br>

## fidden_field
非表示のフォームを作成して、値を隠して渡す
  
(例)フォームは非表示の状態で`user_id`に`current_user.id`を渡して送信する
```rb
<%= form_with model: item, local: true do |form| %>
  <%= form.hidden_field :user_id, value: current_user.id %>
<%= form.submit "投稿する", class: "btn btn-info" %>
<% end %>
```

<br>

## hidden_field_tag
非表示のフォームを作成して、値を隠して渡す(単体でも使用可能)
```rb
<%= hidden_field_tag :カラム名, 値 %>
```
  
(例)フォームは非表示の状態で`user_id`に`current_user.id`を渡して送信する
```rb
<%= hidden_field_tag :user_id, current_user.id %>
```
  
<br>

## readonly: true
読み取り専用のフォームにする
```rb
<%= form.text_field :name, class: "form-control", readonly: true %>
```
  
<br>
  
## form.collection_select
[Rails ドキュメント](https://railsdoc.com/page/collection_select)
```rb
<%= form.collection_select :保存するカラム名, オブジェクトの配列の情報, カラムに保存する項目, セレクトボックスの選択肢の項目, オプション, HTML属性 %>
```
(例)`name`をセレクトボックスで表示して`id`を`user_id`カラムに保存
```rb
<%= form.collection_select :user_id, User.all, :id, :name, include_hidden: false %>
```
