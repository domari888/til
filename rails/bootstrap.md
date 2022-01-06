# Bootstrap 4
bootstrap4 には jQuery と popper.js のインストールが必須  


## インストール
- 必要なyarnパッケージも追加する
  
```
yarn add bootstrap jquery popper.js 
```
  
## インクルード
### `app/javascript/packs/application.js`に追記
- bootstrap の javascript ファイルを読み込めるようにする
  
```js
require("bootstrap/dist/js/bootstrap")
```
> 私たちはjQueryをyarnでインストールしているので、bootstrap自身がjQueryを自動でrequireできるのです。jQueryはapplication.jsの中で利用可能な状態になるので、jQueryをapplication.jsでrequireする必要はありません。すなわち、jQueryをapplication.jsの中で直接使う必要がない限り、実際にはjQueryをapplication.jsでrequireする必要はありません。  
  
### `application.cssをapplication.css`に追記
  
- `application.cssをapplication.scss`にリネームし、コメントやSprockets用の指示を全部空にする
- (注) bootstrap には Reboot.css が含まれているため、他の css ファイルより先に記述しないと全て上書きされてしまう
  
```rb
@import 'bootstrap/scss/bootstrap';
```
  
## jQuery を他の pack でも使用可能にする
### `config/webpack/environment.js` に追記
- (注) `view`では使用不可
   
```rb
const { environment } = require('@rails/webpacker')

const webpack = require('webpack')
environment.plugins.append('Provide', new webpack.ProvidePlugin({
    $: 'jquery',
    jQuery: 'jquery',
    Popper: ['popper.js', 'default']
}))

module.exports = environment
```
jqueryを自動的にロードするには、jqueryが公開している両方の変数を、対応するnodeモジュールに指定する。
- `ProvidePlugin`を使用することで自動的にモジュールをロードして、変数`$`,`jQuery`で`jquery`
モジュールを使用できるようにする。(import/requireを使わずにモジュールを使用することができる。)
- `append`で要素を追加できる
  
## form_with の書き方
- セレクトボックス
```rb
<div class="form-group">
  <%= f.label :age %>
  <%= f.select :age, {'10歳代': 1, '20歳代': 2, '30歳代': 3}, { include_blank: '選択してください'}, { class: 'form-control' , required: true } %>
</div>
```
- enum_help を使った日本語表示
```rb
<div class="form-group">
  <%= f.label :age %>
  <%= f.select :age, User.ages_i18n.invert.keys.map {|k|[k, k]}, {include_blank: '選択してください'}, class: 'form-control' , required: true %>
</div>
```
  
## Navber
- ナビバー内の各要素を 100% 幅で均等に配置
```rb
  <div class="navbar-nav w-100 justify-content-between">
     .
     .
  </div>
```
- `w-100` で幅を 100% にする
- `justify-content-between` で均等に配置
  
<br>

## 上下左右中央に配置
- 配置したい要素の親要素のクラスに`d-flex align-items-center justify-content-center`定義
  
```rb
  <div class="d-flex align-items-center justify-content-center">
    配置したい要素
  </div>
```
(例)`users`テーブルの`image`画像を上下左右中央に配置
```rb
  <div class="d-flex align-items-center justify-content-center">
   <%= image_tag user.image.url, class: "img-fluid" %>
  </div>
```
- `img-fluid`　でアスペクト比を保ったままレスポンシブ対応する
  
## メディアクエリを使用する
scss ファイルに書き込む
```scss
@media (min-width: 992px) {
  .app-name {
    position: absolute;
    top: 10px;
    left: 50%;
  }
}
```
