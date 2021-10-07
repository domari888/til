# Set
  
配列から重複を削除する
  
(順序は要素を投入した順が保持されます)
  
```js
let array1 = [1, 2, 3, 4, 1, 2];

let array2 = Array.from(new Set(array1));

console.log(array2);
  => [1, 2, 3, 4]
```
