## exclude?
引数で指定した値が`含まれていない`か確認する
- 含まれていない場合は`true`
- 含まれている場合は`false`
  
参考 : [Ruby 3.1 リファレンスマニュアル](https://docs.ruby-lang.org/ja/latest/method/Rake=3a=3aFileList/i/exclude.html)
  
 ### 配列
```rb
array = ["a", "b", "c"]

array.exclude?("d")
 #=> true

array.exclude?("a")
 #=> false
```
  
### 文字列
```rb
"abc".exclude?("d")
 #=> true

"abc".exclude?("a")
 #=> false
```
