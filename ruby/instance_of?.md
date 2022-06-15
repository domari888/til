# instance_of?
オブジェクトが特定のクラスのインスタンスかどうか調べる  
結果は真偽値で変える
  
```rb
オブジェクト.instance_of?(クラス名)
```
  
(例)オブジェクトのクラスが`Array`か調べる
```rb
[1, 2, 3].instance_of?(Array)

#=> true

hash = {red: '赤', blue: '青'}
hash.instance_of?(Array)

"=> false
```
