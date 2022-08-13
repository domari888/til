## メイラー
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
