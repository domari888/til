# getElementById メソッド
  
- 任意の HTML タグで指定した id の要素を取得する
  
```html
<html>
 <body>
 
  <p id="greet">Hello!</p>
 
  <script>
   console.log(document.getElementById("greet").textContent);
  </script>
 
 </body>
</html>
```

```html
  #=> Hello!
```
  
- 指定した id がない場合は `null` を返す
  
```html
<html>
 <body>
 
  <p id="greet">Hello!</p>
 
  <script>
   console.log(document.getElementById("color").textContent);
  </script>
 
 </body>
</html>
```

```html
  #=> null
```
  
- 指定した id が重複している場合は最初に一致した要素を取得する
  
```html
<html>
 <body>
 
  <p id="greet">Hello!</p>
  <p id="greet">goodmorning!</p>
 
  <script>
   console.log(document.getElementById("greet").textContent);
  </script>
 
 </body>
</html>
```

```html
  #=> Hello!
```
  
## `innerHTML`を使う
- ボタンをクリックすると関数が実行されて、`<p>`タグ内の文字列を変更する
  
```html
<html>
 <body>
 
  <p id="greet">こんにちは！</p>
  <input type="button" value="Click" onclick="myfunc()">
 
  <script>
   var myfunc = function(){
   document.getElementById("greet").innerHTML = "こんばんは！";
   }
  </script>
 
 </body>
</html>
```

```html
  #=> こんばんは！
```
  
## `onclick` を使用する
- ボタンをクリックすると関数が実行されて、`<input>`タグ内の `value` 属性の値を変更する
  
```html
<html>
 <body>
 
  <input type="button" id="greet" value="Click">
 
  <script>
   var btn = document.getElementById("greet");
   var action = function(){
    btn.value = "Hello world!";
   }
   btn.onclick = action;
  </script>
 
 </body>
</html>
```

```html
  #=> Hello world!
```
  
