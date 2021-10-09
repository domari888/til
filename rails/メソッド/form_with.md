# form_with
  
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

