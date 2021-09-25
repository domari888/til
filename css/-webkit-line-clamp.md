# -webkit-line-clamp
テキストを複数行で省略表示する
  
(例)`class="text"`を持つ要素のテキストを`3行で`省略表示する
```css
.text {
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 3;
  overflow: hidden;
  width: １００％;
}
```
【注】
- `display: -webkit-box;`と`-webkit-box-orient: vertical;`を記載しないと` -webkit-line-clamp:`が有効にならない。
- `Firefox`や`IE`には未対応
