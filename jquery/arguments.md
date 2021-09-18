# arguments
配列風オブジェクト。
`length`以外の配列オブジェクトを持っていない。

参考 : [配列風オブジェクトを配列に展開する](https://www.konosumi.net/entry/2019/05/26/220321)
  
参考 : [arguments - JavaScript | MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Functions/arguments)
  
参考 : [Array.prototype.slice() - JavaScript | MDN](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)
  
参考 : [Removing elements from dropped FileList](https://stackoverflow.com/questions/15136624/removing-elements-from-dropped-filelist)
  
<br>

## Array.prototype.slice.call(arguments);
本物の配列を新しく作成する
  
(例)`dataBox.files`の配列を作成する
```js
//DataTransferオブジェクトで、データを格納する箱を作る
let dataBox = new DataTransfer();
    
Array.prototype.slice.call(dataBox.files);
```

<br>

### 最後の要素を取得する
**`.slice()`を使用しているため`-1`で取得することができる**
  
(例)`dataBox`の`最後の file`を取得する
```js
//DataTransferオブジェクトで、データを格納する箱を作る
let dataBox = new DataTransfer();
    
Array.prototype.slice.call(dataBox.files, -1)[0];
```

(例)`[]`を使って簡略化することができるが、空配列を作成する
```js
[].slice.call(dataBox.files, -1)[0];
```

<br>

### [].slice.call()
Array.prototype.slice.call(arguments)　の簡略化した書き方

```js
[].slice.call(arguments);
```

<br>

### Array.from()
Array.prototype.slice.call(arguments)　の新しい書き方

```js
Array.from(arguments);
```

<br>

### スプレット構文
Array.prototype.slice.call(arguments)　の新しい書き方
  
```js
[...arguments];
```
