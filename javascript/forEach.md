# forEach
  
繰り返し処理を行う。
- 空の要素には何も行わない
- `Break`文は使用できないので、途中で抜け出すことはできない
  
```js
const array = [1, 2, 3, '', '', 4, 5]

array.forEach(function(e){
  console.log(e);
}
```
```
[1, 2, 3, 4, 5]
```
### break を使用
```js
const array = [1, 2, 3, '', '', 4, 5]

array.forEach(function(e){
  console.log(e);
  if(e === 3){
  break;
  }
}
```
```
[1, 2, 3, 4, 5]
```
