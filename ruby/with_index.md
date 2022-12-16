# with_index メソッド
`Enumerator`クラスのインスタンスメソッドで、繰り返し処理でインデックスを取得する事ができる
## 要素のインデックスを取得する
(例)`map`メソッドで使用する
```rb
languages = ['Ruby', 'PHP', 'Python']

languages.map.with_index { |language, i| puts "#{i}: #{language}" }
#=> ["0: Ruby", "1: PHP", "2: Python"]
```
