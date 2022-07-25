## ActiveModel::Attributes
`FormObject`や`データベースと紐づかないクラス`でインクルードすることで、`attr_accesor`の代わりに属性を指定することができ、`型`や`デフォルト値`を指定することができる。  
モデルにカラムがなくても定義できる。
  
(例)無いカラムを定義する。
- users テーブル
  
|      |  users  |
| ---- | ---- |
|  PK  |  id  |
|      |  email  |
|      |  password  |
  
- フォームオブジェクト
```rb
class UserForm < ApplicationRecord
  include ActiveModel::Attributes

  attribute :time_zone, :string, default: -> { Time.zone.name }
end
```
