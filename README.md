# アプリケーション名
Protospace

# アプリケーション概要
アプリケーションを開発しているユーザーが、プロトタイプについてフィードバックを得られるサービスです。ユーザーは、新規登録後に、画像付きでプロトタイプの情報を投稿することができます。投稿内容は編集、削除可能です。そしてコメント欄にて、他のユーザーからフィードバックを得られます。また、ユーザーページにて、ユーザーの詳細情報や、そのユーザーが投稿したプロトタイプの一覧も見ることができます。

# データベース設計

[![Image from Gyazo](https://i.gyazo.com/d915ba8d9261c613741d827b872eebcc.png)](https://gyazo.com/d915ba8d9261c613741d827b872eebcc)

# テーブル設計

## usersテーブル

| Column                | Type         | Options                   |
| --------------------- | ------------ | ------------------------- |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false               |      
| name               | string | null: false               |
| profile            | text   | null: false               |
| occupation         | text   | null: false               |
| position           | text   | null: false               |

### Association

- has_many :prototypes
- has_many :comments


## prototypesテーブル

| Column                | Type         | Options                   |
| --------------------- | ------------ | ------------------------- |
| title       | string     | null: false                    |
| catch_copy  | text       | null: false                    |
| concept     | text       | null: false                    |
| user        | references | null: false, foreign_key: true |

### Association

- has_many :comments
- belongs_to :user


## commentsテーブル

| Column                | Type         | Options                   |
| --------------------- | ------------ | ------------------------- |
| content |text | null: false |                     
| prototype | references | null: false, foreign_key: true |
| user |references | null: false, foreign_key: true |


### Association

- belongs_to :user
- belongs_to :prototype

# 画面遷移図
[![Image from Gyazo](https://i.gyazo.com/5e3c7e5b54e46e83fb590f89a50b6138.png)](https://gyazo.com/5e3c7e5b54e46e83fb590f89a50b6138)

# 開発環境

- フロントエンド
  - HTML,CSS
- バックエンド
  - Ruby on Rails(Ruby)
- データベース
  - MySQL
- タスク管理
  - Github

