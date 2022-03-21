# モデルスペック
  
## エラーを検証する
```rb
expect { # 検証するもの }.to raise_error( #期待するエラー )
```
  
<br>
  
## Form Object を使用したモデルスペックの書き方
`spec/forms`ディレクトリを作成して、配下にフォームオブジェクト用のテストファイルを作成
(例)`PostForm`のモデルスペックファイルを作成
```
mkdir spec/forms
```
```
touch spec/forms/post_form_spec.rb
```
- `spec/forms/post_form_spec.rb`にテストを作成
```rb
require 'rails_helper'

RSpec.describe PostForm, type: :model do
  describe 'バリデーション' do
    subject { post_form.valid? }

    context 'データが条件を満たすとき' do
      let(:post_form) { build(:post_form) }
      it '保存できること' do
        expect(subject).to eq true
      end
    end
  end
end
```
