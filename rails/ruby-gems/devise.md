## ログイン機能実装

### devise をインストール
- Gemfile に下記を追記
```ruby
gem 'devise'
```

### devise の設定ファイルを作成
- devise 専用のコマンドを使用して設定ファイルを作成
```ruby
rails g devise:install
```

### devise を使用する User モデルの作成
- devise 専用コマンドを使用してモデルを作成
```ruby
rails g devise User
```
### ログインページを多言語化
- Gemfile に下記をインストール
```ruby
gem 'rails-i18n', '~> 6.0'
gem 'devise-i18n'
```

- ログインページを日本語化する為に,config/application.rb に下記を追記
```ruby
config.i18n.default_locale = :ja
```

- `created_at` カラムを日本語化する為に,config/application.rb に下記を追記
```ruby
config.time_zone = 'Asia/Tokyo'
```

### devise のビューファイルを生成
- 多言語対応（ devise-i18n 導入が必要）
```ruby
rails g devise:i18n:views
```
- 英語表記
```ruby
rails g devise:views
```
### ログインしていないときにログインページにリダイレクトさせる
- `app/controllers/application_controller.rb`の一番上に追記
```ruby
class ApplicationController < ActionController::Base
  before_action :authenticate_user!
end
```
- 指定したページのリダイレクトを除外( index のページを除外しています )
```ruby
before_action :authenticate_user!, except: :index
```
  
- 指定したコントローラ名、アクション名以外の時、ログイン画面へリダイレクトする
(例)homes コントローラの index アクション以外の時はログイン画面へリダイレクト
```rb
class ApplicationController < ActionController::Base
  before_action :authenticate_user!, if: :controller_name?

  def controller_name?
    unless controller_name == 'homes'　＆＆　action_name == 'index'
      true
    end
  end
end
```
  
### 追加のパラメータを渡す
- 新規登録の際にユーザーネームを追加で渡す場合`app/views/devise/registrations/edit.html.erb
`に下記を追記
```ruby
<div class="field">
  <%= f.label :nickname, "ユーザーネーム" %><br />
  <%= f.text_field :username, autofocus: true %>
</div>
```
- 追加のパラメータを渡す場合、`ApplicationController`で`before_action`を使って渡す。
```ruby
class ApplicationController < ActionController::Base
  before_action :configure_permitted_parameters, if: :devise_controller?

  protected

  def configure_permitted_parameters
    devise_parameter_sanitizer.permit(:sign_up, keys: [:username])
  end
end

```
### ユーザーがログインしているかどうかを真偽値で返す
```ruby
user_signed_in?
```
- ログインしている時、していない時で処理を分ける
```ruby
if user_signed_in?
 # true の処理
else
 # false の処理
end
```
  
## アカウント画像登録
**devise/registrations/new.html.erb**
```rb
  <div class="form-group">
    <%= f.label :avater do %>
      <p><%= image_tag @user.avater.url, class: "rounded-circle", id: 'preview'%></p>
      <%= f.file_field :avater, class: 'previewImage', accept: 'image/png,image/jpeg,image/gif', style: 'display:none;'%>
    <% end %>
  </div>
```
**javascript/packs/preview.js**
```js
document.addEventListener('turbolinks:load', () => {
    const previewImage = document.querySelector('.previewImage');
    previewImage.addEventListener('change', (e) => {
        const fileReader = new FileReader();
        fileReader.onload = (function() {
        document.getElementById('preview').src = fileReader.result;
    });
    fileReader.readAsDataURL(e.target.files[0]);
    });
})
```
- `img_tag` と `file_field` を `do ~ end` で囲むことで画像をクリックする事でファイル選択する事ができるようになる
- `style: 'display:none;'`とすることで入力ボタンを非表示にする事ができる
