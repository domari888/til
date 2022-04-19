# Redcarpet の導入
Rails でマークダウンを記述できるようにする

## 導入方法
`Gemfile`に記述してインストール
```rb
gem 'redcarpet'
```
```
bundle install
```
  
## 使用方法
```erb
<p>
  <% renderer = Redcarpet::Render::HTML %>
  <% extensions = { マークダウンで表示する際の設定 } %>
  <% markdown = Redcarpet::Markdown.new(renderer, extensions) %>
  <%= markdown.render(マークダウンで表示したいテキスト).html_safe %>
</p>
```
  
### ヘルパーメソッドを使用して記述
ヘルパーメソッドを記述するファイルを作成
```
rails g helper markdown
```
`app/helpers/markdown_helper.rb`
```rb
module MarkdownHelper
  def markdown(text)
    markdown = Redcarpet::Markdown.new(html_renderer, markdown_extensions)
    markdown.render(text).html_safe
  end

  private

  def html_renderer
    Redcarpet::Render::HTML
  end

  # マークダウンで表示する際の設定
  def markdown_extensions
    {
      autolink: true,
      space_after_headers: true,
      no_intra_emphasis: true,
      fenced_code_blocks: true,
      tables: true,
      hard_wrap: true,
      xhtml: true,
      lax_html_blocks: true,
      strikethrough: true
    }
  end
end
```
```erb
<p>
  <%= markdown(マークダウンで表示したいテキスト) %>
</p>
```
