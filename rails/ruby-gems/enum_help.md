# enum_help
  
## enum を使った書き方
- 複数の列挙子を一つの列挙型にまとめることができる。
  - データベースでは数値で保存しているため、データ容量が小さくすみ、処理速度が早い
  - 数値で保存しているため、何を表しているかわからない
  
(例)`app/models/colors.rb`
  
```rb
class colors < ApplicationRecord
enum genre: {
  red: 1,
  blue: 2,
  yellow: 3,
  green: 4,
  pink: 5
}
```
```
color = Color.find_by(genre: 5)
color.genre
  #=> "pink"
  
post.genre_before_type_cast
  #=> 5
  
Post.genres
  #=> {"red"=>1, "blue"=>2, "yellow"=>3, "green"=>4, "pink"=>5}
```
  
## enum_help の設定
  
### インストール

```rb
gem 'enum_help'
```
  
### 表示名を変更
  
- `config/locale/enum.ja.yml`を作成して追記
  
```rb
ja:
  enum:
    color:
      genre:
        red: "レッド" 
        blue:　"ブルー"
        yellow:　"イエロー"
        green:　"グリーン"
        pink:　"ピンク"
```
```
post = Post.find_by(genre: "red")
post.genre_i18n
  #=> "レッド"
  
Post.genres_i18n
  #=> {"red"=>"レッド", "blue"=>"ブルー", "yellow"=>"イエロー", "green"=>"グリーン", "pink"=>"ピンク"}
```
  
## セレクトボックス で 日本語訳を表示
- `include_blank: '選択してください'`をつけることでセレクトボックスの一番初めに表示する事ができる
  - 選択しても保存されない
- `required: true`をつけることで入力必須とする
```rb
<div class="form-group">
  <%= f.label :genre %>
  <%= f.select :genre, Color.genres_i18n.invert.keys.map {|k|[k, k]}, include_blank: '選択してください', class: 'form-control' , required: true %>
</div>
```
  

