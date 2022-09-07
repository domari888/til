# carrierwave


## Uploader とは
レコード保存時の`バリデーション`, `ファイル形式`, `ファイルサイズ`などを設定することができる
アップローダーを生成する
```
rails g uploader アップローダー名
```

  
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
  
<br>

## インターネット上にある場所からURLを介してファイルをアップロードする
`remote_カラム名_url`とすることで外部API などを使って取得した画像URLを保存するときなどにも`Uploader`を使って画像保存することができる
  
参考:  
[CarrierWave - GitHub](https://github.com/carrierwaveuploader/carrierwave#uploading-files-from-a-remote-location)  
[URLからCarrierWaveに保存](https://qiita.com/joaoki0412/items/64cb44592923bde2e8ff#-url%E3%81%8B%E3%82%89carrierwave%E3%81%AB%E4%BF%9D%E5%AD%98)  
[carrierwaveuploader/carrierwave](https://github.com/carrierwaveuploader/carrierwave/blob/229594fb2ac7cfa59586162c0b3fc3d0b5bab978/lib/carrierwave/mount.rb#L161)
  
```erb
<%= form_with model: item, local: true do |f| %>
  <%= f.text_field :remote_image_url %>
<% end %>
```
```rb
class ItemsController < ApplicationController
  def create
    @item = current_user.items.build(item_params)
    if @item.save
      redirect_to user_items_path, notice: "アイテムを追加しました"
    else
      redirect_to user_items_path, alert: 'アイテムを追加することができませんでした'
    end
  end
  
  private
  
  def item_params
    params.require(:item).permit(:name, :genre, :remote_image_url)
  end
end
```
  
<br>
  
## RSpec でテスト用画像を設定する
テスト用画像は`spec/fixtures`配下に追加する
(例)`spec/fixtures/test.jpg`　の画像をテストで使用する
```rb
Rack::Test::UploadedFile.new(Rails.root.join('spec/fixtures/test.jpg'))
```
(例)　Factory で Item モデルの image に画像を追加する
```rb
FactoryBot.define do
  factory :item do
    image { Rack::Test::UploadedFile.new(Rails.root.join('spec/fixtures/test.jpg')) }
  end
end
```
