# kaminari
ページネーション処理
  
## API
```rb
@item.total_count #=> レコード総数
@item.offset_value #=> オフセット
@item.num_pages #=> 総ページ数
@item.per_page #=> 1ページごとのレコード数
@item.current_page #=> 現在のページ
@item.first_page? #=> 最初のページならtrue
@item.last_page? #=> 最後のページならtrue
```
[参照記事](https://qiita.com/nysalor/items/77b9d6bc5baa41ea01f3)
  
## 検索処理と併用
Active Record を使った検索処理と併用する場合は、先にデータを取得してからページネーション処理を実行する
(例)ジャンルが`toy`のデータを１ページ１０件ずつ表示
```rb
Item.where(genre: "toy").page(params[:page]).per(10)
```
【NG】
```rb
Item.page(params[:page]).where(genre: "toy").per(10)
```

<br>

## 日本語化
```yml
ja:
  views:
    pagination:
      first: "&laquo;"        # <<
      last: "&raquo;"         # >>
      previous: "&lsaquo;"    # <
      next: "&rsaquo;"        # >
      truncate: "&hellip;"    # ...
```

<br>

## ページネーション時のパラメータ名を変更する
  
ページネーションのテンプレートを渡す際に`param_name: パラメータ名`とすることで、コントローラで指定したパラメータ名でページ番号を受け取ることができる
- デフォルトでは`params[:page]`
  
(例)`params[:post_page]`でページ番号を受け取る
```rb
<%= paginate @posts, param_name: "post_page" %>
```

<br>

## ページネーション時のパラメータに追加
  
ページネーションのテンプレートを渡す際に`params: { 〇〇: "XX" }`とすることでパラメータを受け取ることができる
(例)`params[:action]`で`new`を受け取る
```rb
<%= paginate @posts, params: { action: "new" } %>
```
