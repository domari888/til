# form_for
form系のヘルパーメソッド。フォームに投稿された内容を保存する際に使用する。(rails5.1からはform_withを推奨)
```erb
<%= form_for モデルのインスタンス do |f| %>
  ~ 処理 ~
<% end %>
```
  
## オプション
### html 属性
(例)`User`モデルのフォームに`class`属性(`user-input`)を付与
```erb
<%= form_for @user, html: { class: 'user-input' } do |f| %>
  ~ 処理 ~
<% end %>
```

### url 属性
(例)コントローラ名(`users`)とアクション(`index`)を明示的に指定
```erb
<%= form_for(@user, url: {controller: 'users', action: 'index' }) do |f| %>
  ~ 処理 ~
<% end %>
```
