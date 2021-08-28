## display: flex;
- 中央寄せ
```css
justify-content: center;
```
  
## display プロパティ
### display: inlineblock
- 横並び & ブロック要素
```css
span {
  display: inlineblock
}
```
  
<br>

## インライン要素を左右中央に配置する

```css
text-align: center; 
```

 ## インライン要素を上下中央に配置する
 
 ```css
 vertical-align: middle; 
 ```
 
 ブロック要素内のインライン要素を上下中央に配置する際はテーブルセル化する
 
 ```css
 display: table-cell;
 ```

<br>

## ブロックレベル要素を左右中央に配置する

```css
margin: 0 auto;
```
  
## ブロックレベル要素を上下中央に配置する
- ブロック要素をインライン要素化する
- インライン化した要素を上下中央に配置

```css
display:inline-block; 
```
