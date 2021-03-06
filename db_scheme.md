# Schema documentation

Generated by MySQL Workbench Model Documentation v1.0.0 - Copyright (c) 2015 Hieu Le

## Table: `Clients`

### Description: 



### Columns: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `id` | INT | PRIMARY, Not null |   | Client id |
| `first_name` | VARCHAR(100) | Not null |   | Client first name |
| `last_name` | VARCHAR(255) | Not null |   | Client last name |
| `email` | VARCHAR(255) | Unique | `NULL` | e-mail address |
| `phone` | INT | Not null, Unique |   | Client phone number |
| `country` | VARCHAR(255) |  | `NULL` | Country |
| `region` | VARCHAR(255) |  | `NULL` | Region |
| `сity` | VARCHAR(255) |  | `NULL` | City |
| `street` | VARCHAR(255) |  | `NULL` | Street |
| `house` | VARCHAR(10) |  | `NULL` | House |
| `apartment` | VARCHAR(50) |  | `NULL` | Apartment |


### Indices: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `id` | PRIMARY |   |
| phone | `phone` | UNIQUE |   |
| email | `email` | UNIQUE |   |
| f_name | `first_name` | INDEX | ' Index on first name ' |
| l_name | `last_name` | INDEX | ' Index on last name ' |
| phone_n | `phone` | INDEX | ' Index on phone number ' |
| e_mail | `email` | INDEX | ' Index on email ' |


## Table: `orders`

### Description: 



### Columns: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `id` | INT | PRIMARY, Not null |   | Order id |
| `client_id` | INT | Not null |   | Client id<br /><br />**foreign key** to column `id` on table `Clients`. |
| `order_date` | DATE |  | `NULL` | Ordered registration date |
| `send_date` | DATE |  | `NULL` | Departure date |
| `payment_state` | ENUM | Not null |   | Payment State |
| `product_id` | INT | Not null |   | Product id<br /><br />**foreign key** to column `id` on table `product`. |
| `sum` | DECIMAL |  | `NULL` | Order price |


### Indices: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `id` | PRIMARY |   |
| client-order | `client_id` | INDEX |   |
| order-product | `product_id` | INDEX |   |


## Table: `product`

### Description: 



### Columns: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `id` | INT | PRIMARY, Not null |   | Product ID |
| `nom_name` | VARCHAR(150) |  | `NULL` | Item Name |
| `description_nom` | TEXT |  | `NULL` | Description nomenclature |
| `price` | DECIMAL |  | `NULL` | Price |


### Indices: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `id` | PRIMARY |   |
| n_name | `nom_name` | INDEX | ' Index on nomenclature name ' |


