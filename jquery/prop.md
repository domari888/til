## prop()
  
指定した要素から取得したい`引数`を指定して取得する

```js
$('div').prop('id');
```
  
### `function()`を使用して条件によって属性値を設定する
  
(例)インデックス番号が`1`だった場合、`id 属性`を`preview`に設定する
```js
$('div').prop('id', function(index) {
  if (index === 1 ) return 'preview'; 
});
```