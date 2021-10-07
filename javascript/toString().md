# toString()
  
配列の要素を比較する
  
## 配列を比較
```js
let arrey1 = [1, 2, 3];
let arrey2 = [1, 2, 3];

let result = (arrey1.toString() === arrey2.toString());

console.log(result);
  => true
```

<br>

## オブジェクトの配列を比較
```js
let arrey1 = [{name: 'Taro', age: '20'}, {name: 'Hanako', age: '10'}];
let arrey2 = [{name: 'Taro', age: '20'}, {name: 'Hanako', age: '10'}];

let result = (JSON.toString(arrey1) === JSON.toString(arrey2));

console.log(result);
  => true
```
