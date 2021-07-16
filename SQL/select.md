# SELECT
- テーブルから取得したい`列`の名前を指定する
  - 複数指定したい場合は`,`で区切る
  - 全ての列を指定したい場合は`*`を記述する
   
### SELECT 列名 FROM テーブル名
(例)`users`テーブルの`name`と`age`を指定して取得
```
SELECT name, age FROM users
```
  
(例)`users`テーブルの全ての列を指定して取得
```
SELECT * FROM users
```
