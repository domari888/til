# Range
値の範囲を表すオブジェクト
  
(例)1から3まで(3も含む)
```rb
(1..3).include?(3)
#=> true
```
(例)1から3まで(3を含まない)
```rb
(1...3).include?(3)
#=> false
```
  
<br>
  
### 配列から指定した範囲の要素を取得する
(例)配列からインデックスが1から３までの要素を取得する
```rb
array = [1, 2, 3, 4, 5]

array[1..3]
#=> [2, 3, 4]
```
  
<br>
  
### case文で使用する
(例)年齢に応じて料金を判断する
```rb
def charge(age)
  case age
  when 0..5
    0
  when 6..12
    300
  when 13..18
    600
  else
    1000
  end
end

charge(3)
#=> 0
charge(12)
#=> 300
charge(18)
#=> 600
charge(20)
#=> 1000
```
  
<br>
  
### 値が連続する配列を作成する
範囲オブジェクトに対して`to_a`メソッドを呼び出すと、値が連続する`配列`を作成する事が出来る。
```rb
(1..3).to_a
#=> [1, 2, 3]

(1...3).to_a
#=> [1, 2]

('a'..'c').to_a
#=> ['a', 'b', 'c']

('a'...'c').to_a
#=> ['a', 'b']
```
  
`[*範囲オブジェクト]`の形式でも、配列を作成する事が出来る。
```rb
[*1..3]
#=> [1, 2, 3]

[*1...3]
#=> [1, 2]
```
  
<br>
  
### 繰り返し処理を行う
(例)1から3までの値に対して繰り返し処理を行う
```rb
sum = 0

(1..3).each {|n| sum += n}

sum
#=> 6
```
  
`step()`メソッドを使用して、値を増やす感覚を指定する
(例)1から10までの範囲内で2回毎に繰り返し処理を行う
```rb
numbers = []

(1..10).step(2) {|n| numbers << n}

numbers
#=> [1, 3, 5, 7, 9]
```
