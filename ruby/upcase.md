# upcase メソッド
全ての小文字を対応する大文字に置き換えて文字列を返す
  
## 文字列.upcase
- 全て大文字で返す

```rb
"Ruby on Rails".upcase
  #=> "RUBY ON RAILS"
```

## 配列.map(&:upcase)
配列から要素を取り出し、大文字に置き換えて新しい配列を返す
  
```rb
array = ["a", "b", "c"]

p array.map(&:upcase)
  #=> ["A", "B", "C"]
