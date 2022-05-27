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

## namespace 属性
`namespase: '名称'`で指定した名称を、コンパイル後生成された HTML の id 属性の先頭に追加される
(例)namespase属性で`edit`を指定
【erb】
```rb
<%= form_with model: @post, namespace: 'edit', local: false do |form| %>
  <%= form.label :content %>
  <%= form.text_area :content %>
<% end %>
```
【生成された html】
```html
<label for='edit_post_content'>
  <input id='edit_post_content'>
</label>
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
### オプション
| オプション | 内容 | 例 |
| - | - | - |
| prompt | 未選択時に表示される文字を設定 | prompt: "選択してください" |
| include_blank | 未選択時に表示される文字を設定 | include_blank: "選択してください" |
| selected | はじめに選択されている状態にする | selected: 選択した状態にする番数 |
| disabled | 選択できない状態にする | disabled: 選択できない状態にする番数 |
| include_hidden: true | パラメータに含まれる空白を排除 | |
  
<br>
  
### required: true
[Required Field on collection_select type field - Stack Overflow](https://stackoverflow.com/questions/35726763/required-field-on-collection-select-type-field#:~:text=As%20per%20the%20syntax%20options%20and%20html_options%20are%20hashes%2C%20so%20you%20need%20to%20enclose%20them%20in%20braces.)
```rb
<%= form.collection_select :user_id, User.order(name: :asc), :id, :name, { include_blank: '選択してください' }, { required: true } %>
```
