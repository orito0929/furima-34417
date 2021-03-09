# テーブル設計

## users テーブル

| Column             | Type   | Options                        |
| ------------------ | ------ | ------------------------------ |
| nickname           | string | null: false                    |
| email_address      | string | null: false, foreign_key: true |
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
| category           | string     | null: false                    |
| status             | string     | null: false                    |
| delivery_fee       | string     | null: false                    |
| shipping_area      | string     | null: false                    |
| days_to_deliver    | string     | null: false                    |
| price              | string     | null: false                    |
| seller             | references | null: false, foreign_key: true |

### Association

- belongs_to :users
- has_one :purchase_records

## purchase_records テーブル

| Column    | Type       | Options                        |
| --------- | ---------- | ------------------------------ |
| user      | references | null: false, foreign_key: true |
| product   | references | null: false, foreign_key: true |

### Association

- belongs_to :users
- belongs_to :products
- has_one :shipping_address

## shipping_address テーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| postal_code        | string     | null: false                    |
| prefectures        | string     | null: false                    |
| municipal_district | string     | null: false                    |
| address            | string     | null: false                    |
| building number    | string     | null: false                    |
| phone_number       | string     | null: false                    |
| user               | references | null: false, foreign_key: true |

### Association

- belongs_to :purchase_records