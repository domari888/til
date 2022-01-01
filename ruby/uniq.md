# uniq
  
重複する要素を除外する
  
## 配列内で重複する要素を除外する
```rb
numbers = [1, 2, 3, 2, 1]

numbers.uniq
 #=> [1, 2, 3]
```
  
## ハッシュ内で値が重複する場合に除外する
- 重複する場合最初の要素以外除外する
```rb
numbers = {red: 1, blue: 2, yellow: 3, pink: 2, green: 1}

numbers.uniq{|key, value| value}
 #=> [[:red, 1], [:blue, 2], [:yellow, 3]]

numbers.uniq{|key, value| value}.to_h
 #=> {:red=>1, :blue=>2, :yellow=>3}
```
