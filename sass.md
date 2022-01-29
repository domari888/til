## &: (アンパサンド)
  
要素の状態をネストして書く
  
(例)`class="target"`を持つ要素にカーソルを重ねた状態・クリックした状態のスタイルを設定
```rb
.target {
  &:hover {
    opacity: 0.5;
  }
  &:active {
    opacity: 1;
  }
}
```
