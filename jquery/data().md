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

