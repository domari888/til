## redirect_back
1つ前のページへ戻る
  
### フラッシュメッセージを表示
[参考文献](https://liefery-it-legacy.github.io/blog/2019/07/03/form-objects-and-active-admin.html#:~:text=redirect_back%20fallback_location%3A%20parent_url%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20flash%3A%20%7B%20error%3A%20I18n.t(%22active_admin.issues.description_required%22)%20%7D)
  
```rb
redirect_back(fallback_location: root_path, flash: { error: "表示するメッセージ" })
```
