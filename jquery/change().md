## change()
指定した要素の中身が変更された際にイベント処理を実行
  
<br>

### タグで指定
(例)`input`の中身が変更された際に処理を実行
```js
$('input').change(function() {
  実行する処理
});
```

<br>

### id で指定
(例)`input`の中身が変更された際に処理を実行
```js
$('#preview').change(function() {
  実行する処理
});
```

<br>

### `.on("change")`で指定
`JavaScript`などで編集された HTML には`.on("change")`を使用しないと効かないらしい
  
(例)`input`の中身が変更された際に処理を実行
```js
$('input').on("change", function() {
  実行する処理
});
```

