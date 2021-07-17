# WHERE.md
  
- 処理を行う対象の`行`を絞り込む際に使用する
  - `SELECT`, `UPDATE`, `DELETE`文で使用可能
  - `INSERT`文では使用できない
## 各命令 WHERE 条件式
- `WHERE`の後ろには`true`か`false`を返す`条件式`を記述する
  - `true`となる`行`のみが対象となる
  - `false`や`unknown`となる`行`は対象外になる
  
(例)`users`テーブルの`age`が２０以上の`name`を抽出
```
SELECT name FROM users WHERE age >= 20
```
## IS NULL
- `NULL`であるかどうかを返す
(例)`users`テーブルの`age`が`NULL`かどうか
```
SELECT * FROM users WHERE age IS NULL
```
  
## IS NOT NULL
- `NULL`でないかどうかを返す
(例)`users`テーブルの`age`が`NULL`でないかどうか
```
SELECT * FROM usres WHERE age IS NOT NULL
```
