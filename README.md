# chat-space DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|email|string|null: false|
|password|string|null: false|
### Association
- has_many :posts
- has_many :posts_chats
- has_many :chats,  through:  :posts_chats

## chatsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many :posts
- has_many :posts_chats
- has_many :users,  through:  :posts_chats

## Users_chatsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|chats_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :chat
- belongs_to :user

## postsテーブル
|Column|Type|Options|
|------|----|-------|
|image|text||
|text|text||
|user_id|integer|null: false, foreign_key: true|
|chats_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :chat
