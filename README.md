# DB設計
## users テーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: true ,index: true|
|email|string|null: false, unique: true|
### Association
- has_many :messages
- has_many :groups, through group_users
- has_many :group_users

## groups テーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many :messages
- has_many :users, through groups_users
- has_many :group_users

## messages テーブル
|Column|Type|Options|
|------|----|-------|
|content|text|
|image|string|
|group_id|references|null: false, foreign_key: true|
|user_id|references|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user

## group_users テーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to : group
- belongs_to :user
