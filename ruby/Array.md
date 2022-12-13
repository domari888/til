# Array
参考 : [class Array (Ruby 3.1 リファレンスマニュアル)](https://docs.ruby-lang.org/ja/latest/class/Array.html)

<br>

## 配列にデフォルト値を設定する
引数に渡した数値の個数分の要素を持つ配列を作成する(デフォルト値は`nil`)
```rb
array = Array.new(3)

array
#=> [nil, nil, nil]
```
第二引数にデフォルト値を指定する
```rb
array = Array.new(3, 0)

array
#=> [0, 0, 0]
```
```rb
array = Array.new(3, 'Ruby')

array
#=> ['Ruby', 'Ruby', 'Ruby']
```
引数に渡した数値の回数分ブロックを呼び、その戻り値をデフォルト値に設定する  
ブロックパラメータはインデックスが渡される
```rb
array = Array.new(3){ |n| n + 1 }

array
#=> [1, 2, 3]
```

<br>

### デフォルト値の参照先について
第二引数に指定したデフォルト値は**同じ文字列オブジェクトを参照している**
```rb
array = Array.new(3, 'Ruby')

array
#=> ['Ruby', 'Ruby', 'Ruby']

# 1番目の要素と2番目の要素は同じオブジェクトIDを参照している
array[0].object_id
#=> 100
array[1].object_id
#=> 100

# 1番目の要素だけ破壊的に変更しようとしても、同じ文字列オブジェクトを参照している為全ての要素に影響してしまう
array[0].upcase!
#=> 'RUBY'
array
#=> ['RUBY', 'RUBY', 'RUBY']
```
ブロックでデフォルト値を渡す事で、ブロックが呼ばれる度に新しいデフォルト値を作成する為、配列の各要素は**別々の文字列オブジェクトを参照する事になる**
```rb
array = Array.new(3) { 'Ruby' }

array
#=> ['Ruby', 'Ruby', 'Ruby']

# 1番目の要素と2番目の要素は別々のオブジェクトIDを参照している
array[0].object_id
#=> 100
array[1].object_id
#=> 110

# 1番目の要素だけ破壊的に変更する事ができる
array[0].upcase!
#=> 'RUBY'
array
#=> ['RUBY', 'Ruby', 'Ruby']
```
