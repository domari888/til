# getElementById メソッド
  
- 任意の HTML タグで指定した id の要素を取得する
  
```html
<html>
 <body>
 
  <p id="greet">Hello world!</p>
 
  <script>
   console.log(document.getElementById("greet").textContent);
  </script>
 
 </body>
</html>
```

```html
  #=> Hello world!
```
