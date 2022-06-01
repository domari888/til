# システムスペック
## Capybara の設定
spec_hepler.rb に capybara の設定を追加する。
  
下記の設定をすることで、実行するタスクによって使うドライバを分ける。 
JavaScript を使ったテストを実行する場合は Chrome を使うように、そうでない場合はデフォルトの Rack::Test ドライバを使う。
```spec_hepler.rb
# See http://rubydoc.info/gems/rspec-core/RSpec/Core/Configuration

require 'capybara/rspec'

RSpec.configure do |config|
  config.before(:each, type: :system) do
    driven_by :rack_test
  end

  config.before(:each, type: :system, js: true) do
    driven_by :selenium_chrome_headless
  end
end
```
  
参考:

[公式](https://github.com/teamcapybara/capybara)
  
[Capybaraチートシート](https://qiita.com/morrr/items/0e24251c049180218db4)
  
[rspec-rails 3.7の新機能！System Specを使ってみた](https://qiita.com/jnchito/items/c7e6e7abf83598a6516d)

<br>
  
## 非表示の file_field に画像ファイルを添付する
`make_visible: true`を追加することで`display: none;`などで非表示にした file_field に画像ファイルを添付する事ができる
  
```rb
attach_file('ロケーター', '画像のパス', make_visible: true)
```
参考:

[How to test file attachment on hidden input using capybara?](https://stackoverflow.com/questions/38049020/how-to-test-file-attachment-on-hidden-input-using-capybara#:~:text=attach_file(%27file%5Bpicture%5D%27%2C%20%27path/to/file.png%27%2C%20make_visible%3A%20true))
  
[Find hidden element in capybara - cucumber - Stack Overflow](https://stackoverflow.com/questions/43908750/find-hidden-element-in-capybara#:~:text=attach_file(%27some_name%27%2C%20file_path%2C%20make_visible%3A%20true))
  
[Capybaraチートシート](https://qiita.com/morrr/items/0e24251c049180218db4#:~:text=%E3%81%AE%E3%81%BF%E6%8A%9C%E7%B2%8B%E3%81%99%E3%82%8B%E3%80%82-,locator,%E3%81%AF%E3%83%A1%E3%82%BD%E3%83%83%E3%83%89%E3%81%94%E3%81%A8%E3%81%AE%E5%85%AC%E5%BC%8F%E3%81%AE%E3%83%AA%E3%83%95%E3%82%A1%E3%83%AC%E3%83%B3%E3%82%B9%E3%82%92%E5%8F%82%E7%85%A7%E3%81%AE%E3%81%93%E3%81%A8%E3%80%82,-%E3%83%9A%E3%83%BC%E3%82%B8%E3%81%AB%E3%82%A2%E3%82%AF%E3%82%BB%E3%82%B9)
  
(例)
```rb
attach_file('post[image]', Rails.root.join('spec/fixtures/test.jpg'), make_visible: true)
```
  
【html】
```html
<label for="post_image">
  <input class="post-image-container" type="file" name="post[image]" id="post_image">
</label>
```
  
【css】
```css
.post-image-container {
  display: none;
}
```

<br>

## 現在のページに画像があるか確認する
$=とすることでその後に続く文字列を含むものを探します。
  
参考:
  
[[RSpec]画像がアップロードされたかテストする方法(Capybara)](https://qiita.com/_akira19/items/021be2d09cad54dd4986#:~:text=%24%3D%E3%81%A8%E3%81%99%E3%82%8B%E3%81%93%E3%81%A8%E3%81%A7%E3%81%9D%E3%81%AE%E5%BE%8C%E3%81%AB%E7%B6%9A%E3%81%8F%E6%96%87%E5%AD%97%E5%88%97%E3%82%92%E5%90%AB%E3%82%80%E3%82%82%E3%81%AE%E3%82%92%E6%8E%A2%E3%81%97%E3%81%BE%E3%81%99%E3%80%82)
```rb
expect(page).to have_selector "img[src$=画像のファイル名]"
```
  
(例)`user.avatar`にプロフィール画像が保存されている場合
  
```rb
expect(page).to have_selector "img[src$='#{user.avatar.filename}']"
```
  
<br>
  
## ページにアクセスする
```rb
visit アクセスしたいページへのパス
```
`visit`でアクセスすると`page`変数に格納される`Capybara::Session`オブジェクトが更新される。

<br>

## 処理の完了を待つ
capybara が処理を待つ時間を設定する(デフォルトでは処理を２秒待つ)
  
(例)待機時間を`10秒`に設定する
```rb
it '処理の完了を待つ'
  using_wait_time(10) do
    # 実行するテスト内容
  end
end
```
