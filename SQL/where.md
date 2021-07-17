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
  
## LIKE %指定した文字列%
- 指定した文字列を含んでいる行を抽出
  
(例)`foods`テーブルから`menu`列の文字列に`バナナ`を含む行
```
SELECT * FROM foods WHERE menu LIKE '%バナナ%'
```
`バナナパフェ`, `チョコバナナ`, `いちごバナナクレープ`などが含まれる
  
## LIKE %指定した文字列
- 指定した文字列で終わる文字列を抽出
(例)`foods`テーブルから`menu`列の文字列が`バナナ`で終わる行
```
SELECT * FROM foods WHERE menu LIKE '%バナナ'
```
`チョコバナナ`などが含まれる
  
## LIKE 指定した文字列%
- 指定した文字列で始まる文字列を抽出
(例)`foods`テーブルから`menu`列の文字列が`バナナ`で始まる行
```
SELECT * FROM foods WHERE menu LIKE 'バナナ%'
```
`バナナパフェ`などが含まれる
