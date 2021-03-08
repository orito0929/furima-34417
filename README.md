# テーブル設計

## users テーブル

| Column          | Type   | Options     |
| --------------- | ------ | ----------- |
| nickname        | string | null: false |
| email_address   | string | null: false |
| password        | string | null: false |
| last_name       | string | null: false |
| first_name      | string | null: false |
| birthday        | string | null: false |

### Association

- has_many :products
- has_many :purchase_records

## products テーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| image              |            |                                |
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
| buyer     | references | null: false, foreign_key: true |

### Association

- belongs_to :users
- has_one :shipping_address

## shipping_address テーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| postal_code        | references | null: false, foreign_key: true |
| prefectures        | references | null: false, foreign_key: true |
| municipal_district | references | null: false, foreign_key: true |
| address            | references | null: false, foreign_key: true |
| phone_number       | references | null: false, foreign_key: true |

### Association

- belongs_to :purchase_records