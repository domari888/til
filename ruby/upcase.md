# upcase メソッド
全ての小文字を対応する大文字に置き換えて文字列を返す
  
<br>

## 文字列.upcase
- 全て大文字で返す

```rb
"Ruby on Rails".upcase
  #=> "RUBY ON RAILS"
```

<br>

## 文字列.upcase!
- `nil`を返す

```rb
"RUBY ON RAILS".upcase!
  #=> nil
```

<br>

## 配列.map(&:upcase)
- 配列から要素を取り出し、大文字に置き換えて配列を返す
- 元の配列は変更されない
  
```rb
array = ["A", "b", "c"]

p array.map(&:upcase)
  #=> ["A", "B", "C"]
  
p array
  #=> ["A", "b", "c"]
```

<br>

## 配列.map(&:upcase!)
- 配列から要素を取り出し、大文字に置き換えて配列を返す
- `"A"`はもともと大文字で置き換えることができないため`nil`が返る
- 元の配列も置き換えられる
  
```rb
array = ["A", "b", "c"]

p array.map(&:upcase!)
  #=> [nil, "B", "C"]
  
p array
  #=> ["A", "B", "C"]
```

<br>

## 配列.map!(&:upcase)
- 配列から要素を取り出し、大文字に置き換えて新しい配列を返す
- 元の配列も置き換えられる
  
```rb
array = ["A", "b", "c"]

p array.map!(&:upcase)
  #=> ["A", "B", "C"]
  
p array
  #=> ["A", "B", "C"]
```

<br>

## 配列.map!(&:upcase!)
- 配列から要素を取り出し、大文字に置き換えて配列を返す
- `"A"`はもともと大文字で置き換えることができないため`nil`が返る
- 元の配列も置き換えられるため、　`"A"`は`nil`に置き換えられる
  
```rb
array = ["A", "b", "c"]

p array.map!(&:upcase!)
  #=> [nil, "B", "C"]
  
p array
  #=> [nil, "B", "C"]
```
