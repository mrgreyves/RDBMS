### Запросы для выборки различных данный

Поиск клиента по имени
```
SELECT first_name, last_name FROM clients WHERE first_name="Василий";
```
Поиск по нескольким критериям (используем серию и номер пасспорта для поиска)

```
SELECT first_name, last_name FROM clients WHERE p_series=5555 and p_number=3333;
```

Поиск тура с ценой больше чем ...

```
SELECT id, tour_name FROM tours WHERE price > 50000;
```

Поиск тура с учетом направления и цены 

```
SELECT id, tour_name FROM tours WHERE route="Europe" and price < 90000;
```

Поиск транспорта  с нужным количеством мест и свободным для бронирования

```
SELECT id, name FROM transport WHERE people >= 5 and status="ready";
```

### Использование inner join, left join

Простое объединение нескольких таблиц

```
SELECT first_name, last_name, payment_state, route, tour_name FROM orders, clients, tours WHERE orders.client_id = clients.id AND orders.tours=tours.id;
```

LEFT JOIN таблиц orders и clients, связь по клиентам

```
SELECT clients.first_name, clients.last_name, orders.client_id, clients.id FROM clients LEFT JOIN orders ON clients.id=orders.client_id;
```

INNER JOIN  объеденяем таблицы clients и orders по id клиентов

```
SELECT clients.first_name, clients.last_name, orders.tours FROM clients INNER JOIN orders ON clients.id=orders.client_id;
```