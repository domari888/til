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
