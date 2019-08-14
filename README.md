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
# chat-space DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|username|string|null: false|
### Association
- has_many :messages
- has_many :comments
- has_many :groups

## mesagesテーブル
|Column|Type|Options|
|------|----|-------|
|title|text|null: false|
|text|text|null: false|
|image|image|null: false|
|user_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group
- has_many :comments

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
### Association
- has_many :messages_groups
- has_many  :messages,  through:  :messages_groups

## messages_groupsテーブル
|Column|Type|Options|
|------|----|-------|
|message_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :message
- belongs_to :group

## commentsテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :message
- belongs_to :user