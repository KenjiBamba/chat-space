# chat-space DB設計

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|email|string|null: false, unique: true|
|password|string|null: false|

### Association
- has_many :groups_users
- has_many :groups,  through:  :groups_userss
- has_many :comments


## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|

### Association
- has_many :groups_users
- has_many :users,  through:  :groups_userss
- has_many :comments


## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user


## commentsテーブル
|Column|Type|Options|
|------|----|-------|
|image|text||
|text|text||
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user
