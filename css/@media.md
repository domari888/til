## @media
指定したメディア種別が指定したメディア特性の状態の場合スタイルを適用する
  
参考 : [@media - CSS: カスケーディングスタイルシート | MDN](https://developer.mozilla.org/ja/docs/Web/CSS/@media#:~:text=%E3%81%8C%E3%81%A7%E3%81%8D%E3%81%BE%E3%81%99%E3%80%82-,%E6%A7%8B%E6%96%87,-%40media%20%E3%82%A2%E3%83%83%E3%83%88%E3%83%AB%E3%83%BC%E3%83%AB%E3%81%AF)
```rb
@media メディア種別 and (メディア特性) {
  # 適用するスタイル
}
```
(例)画面幅が576px以下の場合のみスタイルを適用する
```rb
@media screen and (max-width: 57６px) {
  .sample {
    padding: 10px;
  }
}
```
メディア種別を省略すると、すべての機器を対象とする
  
参考 : [@media - CSS: カスケーディングスタイルシート | MDN](https://developer.mozilla.org/ja/docs/Web/CSS/@media#:~:text=not%20%E3%81%BE%E3%81%9F%E3%81%AF%20only%20%E8%AB%96%E7%90%86%E6%BC%94%E7%AE%97%E5%AD%90%E3%82%92%E4%BD%BF%E7%94%A8%E3%81%99%E3%82%8B%E5%A0%B4%E5%90%88%E3%82%92%E9%99%A4%E3%81%8D%E3%80%81%E3%83%A1%E3%83%87%E3%82%A3%E3%82%A2%E7%A8%AE%E5%88%A5%E3%81%AF%E7%9C%81%E7%95%A5%E5%8F%AF%E8%83%BD%E3%81%A7%E3%81%82%E3%82%8A%E3%80%81%E6%9A%97%E9%BB%99%E3%81%A7%20all%20%E3%81%A8%E8%A6%8B%E3%81%AA%E3%81%95%E3%82%8C%E3%81%BE%E3%81%99%E3%80%82)
  
```rb
@media (max-width: 57６px) {
  .sample {
    padding: 10px;
  }
}
```
