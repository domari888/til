# to_ints メソッド
`16進数`を`10進数`に変換して返す(受け取ったRGBカラーを表す16進数の文字列を、R, G, Bそれぞれ10進数に変換して返します。)
  
```rb
to_ints('#ffffff')
#=> [255, 255, 255]

to_ints('#000000')
#=> [0, 0, 0]
```
