# text-overflow: ellipsis
複数行の文字列を`1行`で省略表示する
  
(例)`class="text"`を持つ要素のテキストを1行に省略する
```css
.text {
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
  width: 100%;
}
```
【表示】`...`で省略される
```
テキストテキストテキストテキストテキスト...
```
