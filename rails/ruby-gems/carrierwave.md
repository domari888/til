# carrierwave

## 画像を複数選択する
- 画像投稿フォームに`multiple: true`を追記する
```erb
<%= form_with model: @post, lovale: true do |f| %>
  <%= f.file_feld :image, multiple: true %>
<% end %>
```
  
- コントローラのストロングパラメータで`image`を複数受け取れるようにする
```rb
  def post_params
    params.require(:post).permit(:content, image: [])
  end
```

- ビューで配列の中身を繰り返し処理で１つずつ取り出す
```erb
<% @post.photos.each do |photo| %>
  <%= image_tag photo.image.url %>
<% end %>
```
