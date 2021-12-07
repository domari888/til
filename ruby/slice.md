# slice
  
ハッシュの中からキーをシンボルで指定して、取り出す

 <br>
 
## key => value のハッシュの形で取り出す
```rb
@users = User.all
```
```rb
@users.map { |user|user.slice(:id, :name) }
 
#=> [{"id"=>1, "name"=>"テストユーザー"}, {"id"=>15, "name"=>"ゲストユーザー"}]
```
  
## value, value の配列の形で取り出す
```rb
@users = User.all
```
```rb
@users.map { |user|user.slice(:id, :name).values }

#=> [[1, "テストユーザー"], [15, "ゲストユーザー"]]
```
