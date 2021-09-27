# position
  
## position:absolute;
絶対配置になる(起点からの位置を指定することができる)
  
| | |
|--------|---------------------------|
| top    |   => 起点の上からの距離を指定  |
| bottom |   => 起点の下からの距離を指定  |
| left   |   => 起点の左からの距離を指定  |
| right  |   => 起点の右からの距離を指定  |
  

(例)`class="preview"`を持つ要素を起点の上から`10px`,右から`20px`に配置
```scss
.preview {
  position:absolute;
  top: 10px;            //=> 起点の上からの距離を 10px に指定
  right: 20px;          //=> 起点の右からの距離を 20px に指定
}
```

<br>

## position: fixed
要素の位置を指定した位置で固定する
  
スクロールの際に固定したままにすることができる
  
(例)`class="flash"`を持つ要素を起点の上から`56px`の位置に固定
```scss
.flash {
  position: fixed;
  top: 56px;
}
```
