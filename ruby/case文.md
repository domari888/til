# case 文
## 配列を使用して複数の値を指定する
`*`(splat演算子)を使用することで配列を複数の条件として展開することができる  
```rb
address = ['tokyo', '東京']
prefectures = '東京'
case prefectures
when *address       # when 'tokyo', '東京'と同じ意味になる
  '東京です'
end
```
