# image_tag
img タグを生成するヘルパーメソッド。
  
## <%= image_tag 'ファイル名' %>
-  public/images の場合
(例)`public/images/fallback/default.png`を指定  
/images で始める
```rb
<%= image_tag '/image/fallback/default.png' %>
```

<br>

### 投稿内容の画像を表示させたい場合

(例)`Post`モデルに`image`カラムがある場合

```rb
<%= image_tag post.image.url %>
```

<br>

(例)`Post`モデルに紐づく`Photo`モデルの`image`カラムを表示させる場合

```rb
<%= image_tag post.photos.first.image.url %>
```
`post.photos` には配列で格納されているため、`first`をつけてインデックスを指定して取り出す。  
そのままでは`image`を取り出せない。

```rb
p post.photos
  #=> [#<Photo:0x00007f915a7ed3d8
  id: 1,
  image: "default.png",
  post_id: 1,
  created_at: Tue, 17 Aug 2021 23:02:21.486497000 JST +09:00,
  updated_at: Tue, 17 Aug 2021 23:02:21.486497000 JST +09:00>]
    
p post.photos.first
  #=> #<Photo:0x00007f915a7ed3d8
  id: 1,
  image: "default.png",
  post_id: 1,
  created_at: Tue, 17 Aug 2021 23:02:21.486497000 JST +09:00,
  updated_at: Tue, 17 Aug 2021 23:02:21.486497000 JST +09:00>
    
p post.photos.first.image.url
  #=> "/uploads/photo/image/1/default.png"
