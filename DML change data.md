### Вставка данных в таблицу

```
INSERT INTO clients (id, first_name, middle_name, last_name,phone,email,description,p_series,p_number,p_issued_by,p_registration)
VALUES (1, "Василий", "Иванович", "Пупкин", "88005553535", "not@emai.com", "", "4444","555555", 12-05-1978, "Address")
```

### Вставка данных в таблицу с использование SELECT
Пример из официальный документации.
Можно использовать для вставки данных из одной таблицы в другую.

```
INSERT INTO tbl_temp2 (fld_id)
  SELECT tbl_temp1.fld_order_id
  FROM tbl_temp1 WHERE tbl_temp1.fld_order_id > 100;
```

### Изменение данных UPDATE

```
UPDATE clients SET email="second@emal.adr" WHERE id=1;
```

### Изменение данных UPDATE с JOIN
Джойним таблицы cliets и clients2 по id. И обновляем поля.

```
UPDATE clients c join clients2 c2 ON c.id = c2.id SET c.phone = i.phone, c.email = c2.email, c.p_registration = c2.p_registration;
```

### Удаление данных DELETE. Удаляем по условию.

```
DELETE FROM clients WHERE id=1;
```

### Слияние Merge
Возможно в MySQL при использовании движка MYISAM.
Создаем 2 одинаковых таблицы(t1,t2). Сливаем их в таблицу total. 
Данный метод не очень хорош, так как "сливает" данные как есть.  
Поле с PK совпадут

```
CREATE TABLE t1 (a INT AUTO_INCREMENT PRIMARY KEY, message CHAR(20));
CREATE TABLE t2 (a INT AUTO_INCREMENT PRIMARY KEY, message CHAR(20));
INSERT INTO t1 (message) VALUES ("Testing"),("table"),("t1");
INSERT INTO t2 (message) VALUES ("Testing"),("table"),("t2");
CREATE TABLE total (a INT NOT NULL, message CHAR(20), KEY(a))
             TYPE=MERGE UNION=(t1,t2) INSERT_METHOD=LAST;
```

Вставляем поля в таблицу, если данные в поле id совпадут то id=id+1

```
INSERT INTO clients (id, first_name, middle_name, last_name,phone,email,description,p_series,p_number,p_issued_by,p_registration)
VALUES (1, "Иван", "Петрович", "Иванов", "8800773535", "not11@emai.com", "", "5555","3333", 09-03-1981, "Address")
ON DUPLICATE KEY UPDATE id=id + 1;
```







