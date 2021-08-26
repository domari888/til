## delegate メソッド
  
`post.user.name`のように user 越しに取得しなくても  
`post.name`のように取得できるようになる。
  
(例)`User` モデルの `name` を委譲する
```rb
class Post < ApplicationRecord
  belongs_to :user
  has_many :photos, dependent: :destroy

  delegate :name, :avater, to: :user, prefix: true
end
```
  
`prefix: true`を追記することで`post.user_name`と取得できるようになる。
