# README

* Ruby version
  5.0.7.2

* db design
# Best-Mail DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|username|string|null: false|
### Association
- has_many :posts
- has_many :comments
- has_many :favorites

## postsテーブル
|Column|Type|Options|
|------|----|-------|
|title|text|null: false|
|text|text|null: false|
|user|references|null: false, foreign_key: true|
### Association
- belongs_to :user
- has_many :comments
- has_many :posts_tags
- has_many  :tags,  through:  :posts_tags
- has_many :favirites

## tagsテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
### Association
- has_many :posts_tags
- has_many  :posts,  through:  :posts_tags

## posts_tagsテーブル
|Column|Type|Options|
|------|----|-------|
|post|references|null: false, foreign_key: true|
|tag|references|null: false, foreign_key: true|
### Association
- belongs_to :post
- belongs_to :tag

## commentsテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
|user|references|null: false, foreign_key: true|
|post|references|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :post

## favoriteテーブル
|Column|Type|Options|
|------|----|-------|
|post|references|foreign_key: true|
|user|references|foreign_key: true|
### Association
- belongs_to :post
- belongs_to :user
