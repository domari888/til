## 条件によって class を追加する方法
  
(例)インデックス番号が`0`の場合のみ`class="active"`を追加
```rb
<div class="<%= "active" if i == 0 %>">
```

<br>

## data 属性を付与
  
[Rails の View(ERB) でカスタムデータ属性を設定したい時の方法](https://bake0937.hatenablog.com/entry/2020/07/13/225940)
  
<br>
  
(例)input に `data属性` を付与する
```rb
<%= form.file_field :image, data: {name: "○○○" }%>
```
【 HTML での表示　】
```html
<input data-name="○○○">
```

