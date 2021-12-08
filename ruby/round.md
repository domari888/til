# round
  
指定した数値を四捨五入する

<br>

(例)
```rb
0.123.round
#=> 0

0.123.round(1)
=> 0.1
```
（例）ユーザーの年齢の平均値を四捨五入
```rb
users=User.all
users.average(:age).round
```
