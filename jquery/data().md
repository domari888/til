# data()
`data-`から始めることで`独自の data属性`を付与することができる

  
(例)`名前`と`年齢`の`data 属性`を付与
```erb
<div data-name="Taro" data-age="20">独自のdata属性</div>
```
  
<br>

## 取得
  
### 要素.data();
  
(例)data 属性を全て取得
```js
const info = $('div').data();

console.log('info');
  //=> { name: "Taro", age: 20 }
```
  
### 要素.data('属性名')
  
(例)data 属性の`name`指定して取得
```js
const info = $('div').data('name');

console.log('info');
  //=> Taro
```
  
<br>

## 設定
***************************************************
`data 属性`で設定した値は jQuery 内で**一時的**に保持される
  
(注)HTML 要素が直接追加されるわけではない
***************************************************
  
### 要素.data(属性値, 値);
  
(例)data 属性に`住所`の`data 属性`を設定
```js
$('div').data('address', 'kanagawa');
```
【実行後】
```erb
<div data-name="Taro" data-age="20", address="kanagawa">独自のdata属性</div>
```
  
```js
const info = $('div').data('address');

console.log('info');
  //=> kanagawa
```
  
<br>

## 変更
  
### 要素.data(属性値, 値);
変更する際は、設定するときと同じやり方で上書きする
  
(例)data 属性の`address`を変更
```js
const info = $('div').data('address');

console.log('info');
  //=> kanagawa
```
  
```js
$('div').data('address', 'tokyo');
```
【実行後】
```erb
<div data-name="Taro" data-age="20", address="tokyo">独自のdata属性</div>
```
```js
const info = $('div').data('address');

console.log('info');
  //=> tokyo
```
  



