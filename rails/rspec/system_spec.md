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
