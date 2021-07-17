# WHERE.md
  
- 処理を行う対象の`行`を絞り込む際に使用する
  - `SELECT`, `UPDATE`, `DELETE`文で使用可能
  - `INSERT`文では使用できない
## 各命令 WHERE 条件式
- `WHERE`の後ろには`true`か`false`を返す`条件式`を記述する
(例)`users`テーブルの`age`が２０以上の`name`を抽出
```
SELECT name FROM users WHERE age >= 20
```
