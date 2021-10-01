# .innerHTML
既存の要素(HTML)を破壊して、新たな要素(HTML)を挿入する
  
```html
<ul id="peview">
  <li>リスト１</li>
  <li>リスト2</li>
  <li>リスト3</li>
</ul>
```
  
```js
const preview = document.getElementById('preview');

preview.innerHTML = '<li>リスト４</li>';
```
【変更後】
```html
<ul id="peview">
  <li>リスト4</li>
</ul>
```
  
【js.erb】
  
(例)`layouts/flash_messages`ファイルをレンダリング
```rb
document.getElementById('preview').innerHTML = '<%= j render("layouts/flash_messages") %>';
```
