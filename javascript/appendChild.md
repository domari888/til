## appendChild
  
### Node.appendChild
- 指定した親ノードの、子ノードリストの末尾に子ノードを追加する
(例)id に`preview`をもつノードの子ノードの末尾に 生成した img(子ノード)を追加する
```js
var preview = document.getElementById("preview");
var img = document.createElement("img");

preview.appendChild(img);
```
