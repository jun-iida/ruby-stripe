# Ruby on Rails6 + Stripe API

参考
https://qiita.com/tomokazu0112/items/89f69c47761ac782ce13#%E9%A1%A7%E5%AE%A2%E7%99%BB%E9%8C%B2

### 顧客管理

1. ユーザーがクレジットカードの登録フォームに自身のクレジットカード情報を入力
1. そのクレジットカード情報がフロントエンドを通して stripe で暗号化される
1. その暗号化されたものをトークンとしてバックエンド（今回使用する Rails 側）に渡す
1. そのトークン（card_token）をもとに Stripe::Customer.create（stripe の顧客登録 API）を行うことで、stripe 側へ顧客情報（クレジットカード情報）を登録する

### 顧客情報の取得

バックエンド側の DB に保存しておくべきものは、基本的に顧客 ID のみ
(取得したい顧客の顧客 ID => Stripe => 顧客のクレジットなどの情報)

### クレジットカード登録

データは Stripe に保存させて、取得したい時に情報をじょうほうを取得する
