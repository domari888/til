# textContent メソッド
-  `<script>` と `<style>` 要素を含む、すべての要素の内容を取得
-  スタイルは反映されない
  
```html
<html>
  <body>
  
   <p id="greet">こんにちは！</p>
   <input type="button" value="Click" onclick="myfunc()">
  
   <script>
    var myfunc = function(){
    var myp = document.getElementById("greet").textContent = "<h1>こんばんは！</h1>";
    }
   </script>
  
  </body>
 </html>
```

```html
  #=> <h1>こんばんは！</h1>
```
