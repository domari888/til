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
  
## エラーメッセージの日本語化
```rb
gem 'carrierwave-i18n'
```
```rb
ja:
  errors:
    messages:
      carrierwave_processing_error: 処理できませんでした
      carrierwave_integrity_error: は許可されていないファイルタイプです
      carrierwave_download_error: はダウンロードできません
      extension_whitelist_error: "%{extension}ファイルのアップロードは許可されていません。アップロードできるファイルタイプ: %{allowed_types}"
      extension_blacklist_error: "%{extension}ファイルのアップロードは許可されていません。アップロードできないファイルタイプ: %{prohibited_types}"
      content_type_whitelist_error: "%{content_type}ファイルのアップロードは許可されていません。アップロードできるファイルタイプ: %{allowed_types}"
      content_type_blacklist_error: "%{content_type}ファイルのアップロードは許可されていません"
      rmagick_processing_error: "rmagickがファイルを処理できませんでした。画像を確認してください。エラーメッセージ: %{e}"
      mini_magick_processing_error: "MiniMagickがファイルを処理できませんでした。画像を確認してください。エラーメッセージ: %{e}"
      min_size_error: "を%{min_size}以上のサイズにしてください"
      max_size_error: "を%{max_size}以下のサイズにしてください"
```
  
<br>

## 画像削除用のチェックボックスを作成
```rb
<%= form.check_box :remove_カラム名 %>
```
(例)`avatar`の削除用チェックボックスを作成
フォームを作成
```rb
<%= form.check_box :remove_avatar %>
```
ストロングパラメータで削除要チェックボックスの値を受け取れるように設定
```
def user_params
  params.require(:user).permit(:remove_avatar)
end
```
