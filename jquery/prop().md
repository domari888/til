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
  
### disabled 属性
指定した要素を無効にする
  
(例)`input`を無効にする
```js
$('input').prop('disabled', true);
```
  
(例)`id="new-button"`を持つ要素を無効にする
```js
$('#new-button').prop('disabled', true);
```

<br>

指定した要素の無効化を解除する
  
(例)`input`を解除する
```js
$('input').prop('disabled',  false);
```
  
(例)`id="new-button"`を持つ要素を解除する
```js
$('#new-button').prop('disabled', false);
```
