# splat 演算子
## 配列を展開する
`*配列`で配列を展開して要素を取り出す
```rb
array = [c, d]

[a, b, *a, e, f]
#=> [a, b, c, d, e, f]
```

<br>

## 可変長変数
```rb
def foo(*bar)
  "#{bar.join('と')}"
end

foo('a', 'b', 'c')
#=> "aとbとc"
```
  
