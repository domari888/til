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

