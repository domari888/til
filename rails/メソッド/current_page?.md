# current_page?
  
引数に指定したパスが表示中のページかどうか判断する

<br>

## prefix で指定
(例)`Post`モデルの`show`アクション
```rb
current_page?(post_path(post))
```
  
## アクションで指定
(例)`Post`モデルの`show`アクション
```rb
current_page?(action: "show")
```
  
## コントローラとアクションを指定
(例)`Post`モデルの`show`アクション
```rb
current_page?(controller: "posts", action: "show")
```
