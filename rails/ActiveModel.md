## エラーメッセージのキーを取得
```rb
モデル.errors.keys

#=> [:キー]
```

<br>

## DB なしでモデルを定義
`ActiveModel::Model`を`include`する
  
参考 :  
[RailsでDBと連携しないModelを作成する](https://qiita.com/Esfahan/items/4954b0eb474a81b34258)
  
```rb
class Sample
  include ActiveModel::Model
end
```
