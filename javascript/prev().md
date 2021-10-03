# prev()
  
指定した要素の直前の要素を取得する
```js
HTML要素.prev()
```
  
(例)
```html
<div>
    <h1>タイトル</h1>
    <p>テキスト1</p>
</div>
```
```js
let title = $('p').prev().text()
  
console.log('title')
  => タイトル
```
