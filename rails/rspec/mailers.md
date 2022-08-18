## メイラー
参考 :  
[Rails6のActionMailer機能をRSpecでテストする方法 - Qiita](https://qiita.com/hiroki_tanaka/items/f8c7759682539d7330cd#rspec)
  
[Mailer specs - RSpec Rails - Relish](https://relishapp.com/rspec/rspec-rails/docs/mailer-specs)
  
[【Rails】Action Mailerチュートリアル](https://sakaishun.com/2021/03/17/action-mailer-tutorial/)
  
<br>
  
`type: :mailer`とすることでメイラーのメソッドを使用できるようになる
```rb
RSpec.describe 'お問い合わせ機能', type: :mailer do
  # テスト
end
```
### ActionMailer のテスト例
いたずらをされた際の対策として、`IPアドレス(:remote_ip)`を保存するとよい
  
【app/controllers/contacts_controller.rb】
```rb
def create
  @contact = Contact.new(contact_params)
  if @inquiry.save
    ContactMailer.user_email(@contact).deliver_now
    redirect_to root_path, notice: 'お問い合わせ内容を送信しました'
  else
    render :index
  end
  
  private

  def contact_params
    params.require(:contact).permit(:name, :email, :content,).merge(remote_ip: request.remote_ip)
  end
end
```
【app/mailers/application_mailer.rb】
```rb
class ApplicationMailer < ActionMailer::Base
  default from: 'from@example.com'
  layout 'mailer'
end
```
【app/mailers/contact_mailer.rb】
  
参考 : [Rails ガイド](https://railsguides.jp/action_mailer_basics.html#%E3%83%A1%E3%82%A4%E3%83%A9%E3%83%BC%E3%81%AE%E3%83%93%E3%83%A5%E3%83%BC)
  
```rb
class ContactMailer < ApplicationMailer
  def user_email(contact)
    @contact = contact
    subject = 'お問い合わせを受付いたしました'
    mail(
      to: contact.email,
      subject: subject
    )
  end
end
```
【spec/mailers/contact_mailer_spec.rb】
```rb
RSpec.describe 'お問い合わせ機能', type: :mailer do
  describe '#user_email' do
    let(:contact) { build(:contact) }
    let(:mail) { ContactMailer.user_email(contact).deliver_now }

    it 'renders the headers' do
      expect(mail.subject).to eq('お問い合わせを受付いたしました')
      expect(mail.to).to eq([contact.email])
      expect(mail.from).to eq(['roomake.contact@gmail.com'])
    end
  end
end
```
