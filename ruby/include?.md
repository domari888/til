# include? メソッド
  
- 対象の文字列や、配列などのオブジェクトに引数で渡した値が含まれているか判断して真偽値で返す
- 含まれていれば`true`、含まれていなければ`false`
  
## 文字列.include?("文字列")

```rb
"hello world".include?("hello")
  #=> true
  
"hello world".include?("rld")
  #=> true
  
"hello world".include?("aaa")
  #=> false
```


## 配列.include?(値)

```rb
["hello", "world"].include?("hello")
  #=> true
  
["hello", "world"].include?("rld")
  #=> true
  
["hello", "world"].include?("helloworld")
  #=> false
```

