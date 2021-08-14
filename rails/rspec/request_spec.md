## リクエストスペック
### example とは
テストの単位のこと。  
`it do .. end`までの一括りのことを指しており、その中にテストを書く。
  
## before
`before do .. end` で囲まれた部分は example 実行前に呼ばれる。　　
`before { .. }`でも記述可能。
(例)example 実行前に before でユーザーを作成
```rb
RSpec.describe User do
  describe "GET #index" do
    before do
     create(:user)
    end
    context "ユーザーが存在するとき" do
      it "name が表示される" do
        expect(user.name).to eq "Taro"
      end
    end
  end
end
