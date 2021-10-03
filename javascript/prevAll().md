# prevAll()
    
指定した要素の前にある全て要素を取得する
- 直前の要素から取得していく
```js
HTML要素.prev()
```
  
(例)
```html
<div>
    <h1>タイトル1</h1>
  　　　　<h２>タイトル2</h2>
    <h3>タイトル3</h3>
    <p>テキスト</p>
</div>
```
```js
let title = $('p').prev().text()
  
console.log('title')
  => タイトル３ タイトル２ タイトル１
```
