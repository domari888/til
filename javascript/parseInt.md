# parseInt
  
文字列を明示的に型を数値に変換する。
```js
parseInt(文字列);
```
(例)文字列`'10'`を数値`10`に変換する
```js
const string = '10';

parseInt(string);
  => 10
```

<br>

**文字列の数値以外の文字は無視されて変換される**
  
(例)文字列`'10番目'`を数値`10`に変換する
```js
const string = '10番目';

parseInt(string);
  => 10
```
