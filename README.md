# テーブル設計

## users テーブル

| Column             | Type   | Options                        |
| ------------------ | ------ | ------------------------------ |
| nickname           | string | null: false                    |
| email              | string | null: false, unique: true      |
| encrypted_password | string | null: false                    |
| last_name          | string | null: false                    |
| first_name         | string | null: false                    |
| last_furigana      | string | null: false                    |
| first_furigana     | string | null: false                    |
| birthday           | date   | null: false                    |

### Association

- has_many :products
- has_many :purchase_records

## products テーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| product            | string     | null: false                    |
| description        | text       | null: false                    |
| category_id        | integer    | null: false                    |
| status_id          | integer    | null: false                    |
| delivery_fee_id    | integer    | null: false                    |
| prefecture_id      | integer    | null: false                    |
| days_to_deliver_id | integer    | null: false                    |
| price              | integer    | null: false                    |
| user               | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- has_one :purchase_record

## purchase_records テーブル

| Column    | Type       | Options                        |
| --------- | ---------- | ------------------------------ |
| user      | references | null: false, foreign_key: true |
| product   | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :product
- has_one :shipping_address

## shipping_address テーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| postal_code        | string     | null: false                    |
| prefecture_id      | integer    | null: false                    |
| municipal_district | string     | null: false                    |
| address            | string     | null: false                    |
| building_number    | string     |                                |
| phone_number       | string     | null: false                    |
| purchase_record    | references | null: false, foreign_key: true |

### Association

- belongs_to :purchase_record