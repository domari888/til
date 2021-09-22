# truncate メソッド
表示する文字数を指定して、長い文字列を省略する
  
(例)`post.content`の文字列を１００文字以降省略する
```rb
<%= truncate(post.content, length: 100) %>
```

<br>
  
## 末尾に付与される`...`を任意の文字に変更
  
(例)`post.content`の文字列の末尾に任意の文字を付与
```rb
<%= truncate(post.content, length: 100, omission: もっと見る) %>
```
