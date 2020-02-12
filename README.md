# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# freemarket_sample_68th DB設計
## usersテーブル
|Column|Type|Options|
|nickname|text|null: false|
|mail|string|null: false|
|password|string|null: false|
|confirm_password|string|null: false|
|name|string|null: false|
|name_zenkaku|string|null: false|
|birthday|data|null: false|
|phone-number|text|null: false|
### Association
- has_one :credit_card
- has_one :useradress
- has_many :products

## creditCardsテーブル
|Column|Type|Options|
|cardnumber|int|null: false|
|month|int|null: false|
|year|int|null: false|
|css_number|int|null: false|


### Association
- has_one :user

## useraddressesテーブル
|Column|Type|Options|
|postal_code|int|null: false|
|city|text|null: false|
|address|text|null: false|
|building|text|null: false|
|phone-number|int|null: false|

### Association
- has_one :user
- has_one :prefecture


## prefectureテーブル
|Column|Type|Options|
|name|text|null: false|

### Association
- has_one :useraddress
- has_many :product

## productsテーブル
|Column|Type|Options|
|name|int|null: false|
|content|text|null: false|
|condition|text|null: false|
|status|text|null: false|
|payment|int|null: false|
|delivery_date|int|null: false|
|derivery_method|int|null: false|
|price|int|null: false|
|user_id|int|null: false, foreign_key: true|
|prefecture_id|int|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :prefecture
- has_many :categories
- has_many :blands
- has_many :images

## imagesテーブル
|Column|Type|Options|
|image|text|null: false|
|product_id|int|null: false, foreign_key: true|


### Association
- belongs_to :product

## blandsテーブル
|Column|Type|Options|
|name|text|null: false|
|product_id|int|null: false, foreign_key: true|


### Association
- belongs_to :product

## categoriesテーブル
|Column|Type|Options|
|parent_category|text|null: false|
|middle_category|text|null: false|
|child_category|text|null: false|
|product_id|int|null: false, foreign_key: true|


### Association
- belongs_to :product

