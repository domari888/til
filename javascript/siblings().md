# siblings()
  
同じ階層の要素をすべて取得する
```html
<div>
    <p class="one">テキスト1</p>
    <p class="two">テキスト２</p>
    <p class="three">テキスト3</p>
    <p class="four">テキスト4</p>
    <p class="five">テキスト5</p>
</div>
```
```js
const result1 = $('.three').siblings('.one');
 
console.log( result1.text() );
  => テキスト１
```
