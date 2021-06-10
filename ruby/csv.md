
# CSV 
- `,` で区切ったデータ形式のファイル
- `require "csv"` で最初に読み込む
  
- （例）[sample.csv]
```
id,name,age
1,ユーザー１,10
2,ユーザー２,1０
3,ユーザー3,30
```
  
## CSV ファイルを読み込む
### CSV.foreach("csvファイルへのパス")
  
- ファイルから一行ずつ読み込む
- `headers：　true` を入れることでCSVファイルのヘッダー情報を読み取る

```ruby
CSV.foreach('ファイル名’, headers: true） do |row|
  p row
end
```
(例)
```ruby
CSV.foreach('sample.csv’, headers: true） do |row|
  p row
end
  #=> ["1", "ユーザー1", "10"]
  #=> ["2", "ユーザー2", "10"]
  #=> ["3", "ユーザー3", "30"]
```
  
### CSV.read("csvファイルへのパス")
  
- ファイルを一度に読み込む

```ruby
data = CSV.read('ファイル名')
p data
  #=> [["1", "ユーザー1", "10"], ["2", "ユーザー2", "10"], ["3", "ユーザー3", "30"]]
```
  
### ハッシュの形式で受け取る

```ruby
datas = []
CSV.foreach('sample.csv') do |row|
  data << {id: row["id"], name: row["name"], age: ["age"]}
end

p datas
  #=> [
  #=>{id: "1", name: "ユーザー1", age: "10"}
  #=>{id: "2", name: "ユーザー2", age: "10"}
  #=>{id: "3", name: "ユーザー3", age: "30"}
  #=>]
```
  
```ruby
dates = CSV.read('sample.csv').map do |row|
  {id: row["id"], name: row["name"], age: ["age"]}
end

p datas
 #=> [
  #=>{id: "1", name: "ユーザー1", age: "10"}
  #=>{id: "2", name: "ユーザー2", age: "10"}
  #=>{id: "3", name: "ユーザー3", age: "30"}
  #=>]
```
  
- id が 1 のデータを指定して受け取る
```ruby
p datas.find( | data | data[:id] = 1 }
  #=> {id: "1", name: "ユーザー1", age: "10"}
```
  
- age が １０ のデータを指定して受け取る
```ruby
p datas.find_all{ | data | data[:age] = 10 }
  #=>{id: "1", name: "ユーザー1", age: "10"}, {id: "2", name: "ユーザー2", age: "10"}
```
  
## CSV ファイルに書き込む

### CSV.open("csvファイルへのパス", "w") do |row|

```ruby
CSV.open("sample2.csv", "w") do|row|
  csv << ["id", "name", "age"]
  csv << ["4", "ユーザー4", "40"]
  csv << ["5", "ユーザー5", "50"]
  csv << ["6", "ユーザー6", "60"]
end
```

- （例）[sample2.csv]

```
id,name,age
4,ユーザー4,40
5,ユーザー5,5０
6,ユーザー6,60
```





