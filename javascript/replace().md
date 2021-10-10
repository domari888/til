# replace()
  
任意の文字列から指定した文字を、別の文字に置き換える

```js
文字列.replace(指定する文字, 置き換える文字)
```
```js
const name = 'Taro_Tanaka';
const user_name = name.replace( '_', '-' );
 
console.log( user_name );
  => Taro-Tanaka
```

<br>

### 正規表現を使用した方法
(例)`g`フラグを使用して、全ての`_`を置き換える
```js
文字列.replace(指定する文字, 置き換える文字)
```
```js
const name = 'Taro_Tanaka, Hanako_Yamada';
const user_name = name.replace( /_/g, '-' );
 
console.log( user_name );
  => Taro-Tanaka, Hanako-Yamada
```
