# Schema documentation

Generated by MySQL Workbench Model Documentation v1.0.0 - Copyright (c) 2015 Hieu Le

## Table: `clients`

### Description: 

clients description

### Columns: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `id` | INT | PRIMARY, Not null, Unique |   |   |
| `first_name` | VARCHAR(50) | Not null |   |   |
| `middle_name` | VARCHAR(50) | Not null |   |   |
| `last_name` | VARCHAR(50) | Not null |   |   |
| `phone` | VARCHAR(50) | Not null |   |   |
| `email` | VARCHAR(50) | Not null |   |   |
| `description` | VARCHAR(500) |  | `NULL` |   |
| `p_series` | INT | Not null |   | Passport Series |
| `p_number` | INT | Not null |   | Passport number |
| `p_issued_by` | VARCHAR(500) | Not null |   | Passport issued by |
| `p_registration` | VARCHAR(500) |  | `NULL` | Place of registration |


### Indices: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `id` | PRIMARY |   |
| id_UNIQUE | `id` | UNIQUE |   |
| lastn_index | `last_name` | INDEX | 'index on last name' |
| email_index | `email` | INDEX |   |
| phone_index | `phone` | INDEX |   |


## Table: `discount`

### Description: 

tours for sale

### Columns: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `id` | INT | PRIMARY, Not null, Unique |   |  **foreign key** to column `id` on table `tours`. |
| `route` | VARCHAR(50) | Not null |   | Direction of the tour (Eroupe, Asia, South-North Amarica, etc.) |
| `days` | INT | Not null |   |   |
| `hotel` | VARCHAR(150) | Not null |   |   |
| `h_num` | INT | Not null |   | number of people\n |
| `tour_name` | VARCHAR(150) | Not null |   |   |
| `day_to_start` | INT | Not null |   |   |
| `disc_price` | DECIMAL(9,2) | Not null |   | discount price |


### Indices: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `id` | PRIMARY |   |
| id_UNIQUE | `id` | UNIQUE |   |


## Table: `events`

### Description: 



### Columns: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `id` | INT | PRIMARY, Not null, Unique |   |  **foreign key** to column `id` on table `tickets`. |
| `name` | VARCHAR(50) | Not null |   |   |
| `days` | INT | Not null |   |   |
| `price` | DECIMAL(9,2) | Not null |   |   |
| `worker` | INT | Not null |   | Employee name<br /><br />**foreign key** to column `id` on table `worker`. |
| `transport` | INT |  | `NULL` | Necessary transport<br /><br />**foreign key** to column `id` on table `transport`. |
| `hotels` | INT | Not null |   | Is accommodation required |
| `description` | VARCHAR(500) | Not null |   | Event description |
| `ticket` | INT |  | `NULL` |   |


### Indices: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `id` | PRIMARY |   |
| id_UNIQUE | `id` | UNIQUE |   |
| worker_to_worker_id_idx | `worker` | INDEX |   |
| transp_to_transp_id_idx | `transport` | INDEX |   |


## Table: `hotels`

### Description: 



### Columns: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `id` | INT | PRIMARY, Not null, Unique |   |  **foreign key** to column `id` on table `events`. |
| `h_name` | VARCHAR(150) | Not null |   |   |
| `price` | DECIMAL(9,2) | Not null |   |   |
| `description` | VARCHAR(500) | Not null |   |   |


### Indices: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `id` | PRIMARY |   |
| id_UNIQUE | `id` | UNIQUE |   |
| h_name_index | `h_name` | INDEX |   |
| desc_index | `description` | FULLTEXT |   |


## Table: `orders`

### Description: 

Order list

### Columns: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `id` | INT | PRIMARY, Not null, Unique |   |  **foreign key** to column `id` on table `clients`. |
| `payment_state` | TINYINT | Not null |   |   |
| `order_date` | DATE | Not null |   |   |
| `tours` | INT |  | `NULL` |  **foreign key** to column `id` on table `tours`. |
| `events` | INT |  | `NULL` |  **foreign key** to column `id` on table `events`. |
| `client_id` | INT | Not null |   |   |


### Indices: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `id` | PRIMARY |   |
| id_UNIQUE | `id` | UNIQUE |   |
| order_to_tours_id_idx | `tours` | INDEX |   |
| event_to event_id_idx | `events` | INDEX |   |


## Table: `tickets`

### Description: 

transport tickets

### Columns: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `id` | INT | PRIMARY, Not null, Unique |   |   |
| `ticket_name` | VARCHAR(100) | Not null |   |   |
| `destination` | VARCHAR(100) | Not null |   |   |
| `departure_from` | VARCHAR(100) | Not null |   | The name of the place of departure |
| `description` | VARCHAR(1000) |  | `NULL` | Ticket description |
| `arrival_date` | DATE | Not null |   | Departure date |


### Indices: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `id` | PRIMARY |   |
| id_UNIQUE | `id` | UNIQUE |   |
| name_index | `ticket_name` | INDEX |   |
| from_index | `departure_from` | INDEX |   |
| dest_index | `destination` | INDEX |   |
| disc_index | `description` | FULLTEXT |   |


## Table: `tours`

### Description: 

Tours provided by the organization

### Columns: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `id` | INT | Not null, Unique |   |   |
| `route` | VARCHAR(50) | Not null |   | Direction of the tour (Eroupe, Asia, South-North Amarica, etc.) |
| `days` | INT | Not null |   |   |
| `hotel` | VARCHAR(150) | Not null |   | Hotel description |
| `h_num` | INT | Not null |   | number of people |
| `tour_name` | VARCHAR(150) | Not null |   |   |
| `price` | DECIMAL(9,2) | Not null |   |   |
| `description` | VARCHAR(500) | Not null |   | Short description\n |
| `t_start_dat` | DATE | Not null |   | Tour start date |


### Indices: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| id_UNIQUE | `id` | UNIQUE |   |
| route_index | `route` | INDEX |   |
| tourn_index | `tour_name` | INDEX |   |
| desc_index | `description` | FULLTEXT |   |


## Table: `transport`

### Description: 

company transport

### Columns: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `id` | INT | PRIMARY, Not null, Unique |   |   |
| `name` | VARCHAR(50) | Not null |   |   |
| `people` | INT | Not null |   | capacity of people |
| `type` | VARCHAR(50) | Not null |   | vehicle type |
| `status` | VARCHAR(50) | Not null |   | vehicle status (available, repair, etc) |


### Indices: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `id` | PRIMARY |   |
| id_UNIQUE | `id` | UNIQUE |   |


## Table: `worker`

### Description: 

Employee data

### Columns: 

| Column | Data type | Attributes | Default | Description |
| --- | --- | --- | --- | ---  |
| `id` | INT | PRIMARY, Not null, Unique |   |   |
| `first_name` | VARCHAR(50) | Not null |   |   |
| `last_name` | VARCHAR(50) | Not null |   |   |
| `middle_name` | VARCHAR(50) |  | `NULL` |   |
| `d_o_b` | DATE | Not null |   | Date of Birth |
| `price_at_month` | DECIMAL(9,2) | Not null |   |   |
| `price_at_day` | DECIMAL(9,2) | Not null |   |   |
| `price_at_event` | DECIMAL(9,2) | Not null |   |   |


### Indices: 

| Name | Columns | Type | Description |
| --- | --- | --- | --- |
| PRIMARY | `id` | PRIMARY |   |
| id_UNIQUE | `id` | UNIQUE |   |


