# defined?
変数が定義されているかチェックする。
`undifined`かどうか判定する
  
```
> hoge
#=> NameError (undefined local variable or method `hoge' for main:Object)

> defined? hoge
#=> nil
```
```
> hoge = "abc"
=> "abc"

> defined? hoge
#=> "local-variable"
```
