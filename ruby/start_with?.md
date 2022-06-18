# start_with?
文字列の先頭が指定したパターンのどれか１つでも当てはまる時　`true`を返す
```rb
'sample'.start_with?('sam')
#=> true

'sample'.start_with?('ple')
#=> false

'sample'.start_with?('text', 'ple', 'sam')
#=> true
```
