# link_to
  
## target: "_blank"
  
新規ウィンドウでリンク先を表示する
  
(例)トップページへのリンクを新しいウィンドウで開く
```rb
<%= link_to "トップページ", root_path, target: "_blank" %>
```

<br>
  
## 二重送信を防止する
クリックした後、二重クリックされないようにリンクを非表示にして`disable_with`で設定した文字列を表示する
  
(例)非同期で実装した`いいね`が二重クリックされないように対策する
```rb
<%= link_to "いいね", post_likes_path(post), method: :post, data: { disable_with: "送信する" }, remote: true %>
```
