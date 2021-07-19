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
