# counter_cache
  
子モデルの数をカウントして親モデルのカラムに保存する

<br>

```rb
belongs_to :`親モデル`, counter_cache: :`親モデルのカラム` 
```

(例)`Post モデル`の`likes_count`カラムに関連付く`Like モデル`の数を保存

```rb
belongs_to :post, counter_cache: :likes_count
```
