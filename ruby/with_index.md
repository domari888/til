# with_index メソッド
`Enumerator`クラスのインスタンスメソッドで、繰り返し処理でインデックスを取得する事ができる
## 要素のインデックスを取得する
(例)`map`メソッドで使用する
```rb
languages = ['Ruby', 'PHP', 'Python']

languages.map.with_index { |language, i| "#{i}: #{language}" }
#=> ["0: Ruby", "1: PHP", "2: Python"]
```

### 開始するインデックスの値を指定する
(例)インデックスが`１`から開始するように指定する
```rb
languages = ['Ruby', 'PHP', 'Python']

languages.map.with_index(1) { |language, i| "#{i}: #{language}" }
#=> ["1: Ruby", "2: PHP", "3: Python"]
```
