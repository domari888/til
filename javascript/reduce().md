# reduce()メソッド
配列の各要素に対して、コールバック関数を呼び出す。
  
直前の要素との処理結果を返り値として、次の要素と計算し、最終的な返り値を`reduce()`メソッドの結果として返す。  
初回実行時には配列の０番目の値を返し、初期値が指定されている場合はその値を返す。

[Array.prototype.reduce() - JavaScript - MDN Web Docs](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)
  
*コールバック関数 - 関数の引数に指定する別の関数のこと

### 初期値がない場合の処理の流れ
```js
const numbers = [1, 2, 3, 4]

const sum = numbers.reduce(function(a, b){
  a + b
});
```
1.　配列[0]が`a`,配列[1]が`b`に渡される  // 1 + 2  
2.　直前の処理結果が`a`、配列[2]が`b`に渡される  // 3 + 3  
3.　直前の処理結果が`a`、配列[3]が`b`に渡される  // 6 + 4  
となり`sum`には`10`が返る。
