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
