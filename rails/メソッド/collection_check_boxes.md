# collection_check_boxes
  
モデルからチェックボックスを自動生成する
  
[参考文書](https://pikawaka.com/rails/form_with#form.collection_check_boxes)
[参考文書](https://pote-chil.com/rails_collection_check_boxes/)

```rb
  <%= form.collection_check_boxes(保存されるカラム名, オブジェクトの配列, カラムに保存される項目, チェックボックスに表示されるカラム名 ) %>
```
  
(例)`Category`モデルの`name`をラベルにしたチェックボックスを作成して、選択した項目の`id`を中間テーブルの`category_id`に保存
- 複数選択されるため`category_ids`としておく
```rb
  <%= form.collection_check_boxes :category_ids, Category.all, :id, :name do |form| %>
```

<br>

## include_hidden: false
送信後のパラメータの配列の最初に value が`""`の `hidden` タグが挿入されるのを防ぐ
```rb
  <%= form.collection_check_boxes :category_ids, Category.all, :id, :name, include_hidden: false do |form| %>
```
