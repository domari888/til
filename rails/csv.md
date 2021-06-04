# CSV インポート
## データを作成
- (例)`user_data.csv`ファイルを`db`ディレクトリに作成
```ruby
mkdir db/csv_data
touch db/csv_data/user_data.csv
```
- csv データを追加
```ruby
name,age,address
tanaka,10,tokyo
satou,20,saitama
itou,30,kanagawa
```
  
## ファイル作成
- `lib` に　データ投入に使用するファイルを作成し追記
  - (例)`import_csv` ファイルを作成
```ruby
touch lib/import_csv.rb
```
  
```ruby
require "csv"

class ImportCsv
  def self.import(path)
    CSV.foreach(path, headers: true) do |row|
      User.create!(
        name: row[:name],
        age: row[:age],
        address: row[:address]
      )
    end
  end
end
```
- `headers: true`
  - csv データの１行目にヘッダーがある場合のみ記入
  
- `row[:列の情報]`　
  - csvデータの列の情報を指定して読み込む
  
- CSV ファイルのカラム名と、テーブルのカラム名が同じ場合
```ruby
require "csv"

class ImportCsv
  def self.import(path)
    CSV.foreach(path, headers: true) do |row|
      User.create!(row.to_h)
    end
  end
end
```
  
## rails c でインポート
- 作成したファイルを読み込む
```ruby
require " 作成したファイル名 "
```
```ruby
# (例)
require "import_csv"
```
  
- ファイルのクラスメソッドを実行
```ruby
クラス名.クラスメソッド名('CSV データのあるファイルのパス')
```
```ruby
# (例)
ImportCsv.import('db/csv_data/user_data.csv')
```
  
