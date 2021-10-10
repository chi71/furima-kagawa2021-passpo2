#  DB 設計

## users table

| Column                | Type           | Options                    |
|-----------------------|----------------|----------------------------|
| nickname              | string         | null: false                |
| email                 | string         | null: false, unique: true  |
| encrypted_password    | string         | null: false                |
| first_name            | string         | null: false   全角          |
| family_name           | string         | null: false   全角          |
| first_name_kana       | string         | null: false   全角          |
| family_name_kana      | string         | null: false   全角          |
| birthday_year         | integer        | null: false                |
| birthday_month        | integer        | null: false                |
| birthday_day          | integer        | null: false                |

### Association

has_many :items
has_one :purchase

## items table

| Column                | Type           | Options                        |
|-----------------------|----------------|--------------------------------|
| item_name             | string         | null: false                    |
| image                 | ASで実装        ｜ null: false                   |(has_one_attached?)        
| explain               | text           | null: false                    |                   
| item_price            | integer        | null: false                    |
| user                  | reference      | null: false, foreign_key: true |
| category              | integer        | null: false                    |
| statement             | integer        | null: false                    |
| load                  | integer        | null: false                    |
| area                  | integer        | null: false                    |
| delivery_days         | integer        | null: false                    |

### Association

belongs_to :user
has_one :purchase

## purchases table

| Column                | Type           | Options                        |
|-----------------------|----------------|--------------------------------|
| postal_code           | string         | null: false                    |
| prefecture            | integer        | null: false                    |
| city                  | string         | null: false                    |
| house_number          | string         | null: false                    |
| building_number       | string         |                                |
| tel_number            | string         | null: false,                   |
| user                  | reference      | null: false, foreign_key: true |
| item                  | reference      | null: false, foreign_key: true |

### Association

belongs_to :user
belongs_to :item