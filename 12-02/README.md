# Домашнее задание к занятию "`Работа с данными (DDL/DML)`" -`Лазебный Кирилл`

---

### Задание 1

`Выполнил запрос на получение списка пользователей в базе данных.`

`Выполнил запрос на получение списка прав для пользователя sys_temp.`

`Скачал и восстановил дамп базы данных и сформировал ER-диаграмму. `

#### Простыня SQL-запросов

```SQL
-- 1.2. Создание учетной записи sys_temp
CREATE USER 'sys_temp'@'localhost' IDENTIFIED BY 'qwerty';

-- 1.3. Получение списка пользователей в базе данных
SELECT user, host FROM mysql.user;

-- 1.4. Выдача всех прав для пользователя sys_temp (на весь сервер)
GRANT ALL PRIVILEGES ON *.* TO 'sys_temp'@'localhost';

-- 1.5. Получение списка прав для пользователя sys_temp
SHOW GRANTS FOR 'sys_temp'@'localhost';

-- 1.6 - 1.8. Восстановление дампа Sakila и ER-диаграмма
-- (Дамп загружен через выполнение скриптов sakila-schema.sql и sakila-data.sql)
```
---

### Задание 2

`Составил таблицу Excel с 2-мя столбцами - название таблиц и название первичных ключей.`

```
Название таблицы	Название первичного ключа
actor	            actor_id
address	          address_id
category	        category_id
city	            city_id
country	          country_id
customer	        customer_id
film	            film_id
film_actor	      actor_id
film_actor	      film_id
film_category	    film_id
film_category	    category_id
film_text	        film_id
inventory	        inventory_id
language	        language_id
payment	          payment_id
rental	          rental_id
staff	            staff_id
store	            store_id
```
<img width="1920" height="1031" alt="1" src="https://github.com/user-attachments/assets/85ef4297-a5d9-4da0-a4ce-56833db50fbf" />

---

### Задание 3

`Выполнил запрос на получение списка прав для пользователя sys_temp после удаления у пользователя следующих прав - (INSERT, UPDATE, DELETE).`


#### Простыня SQL-запросов

```SQL
-- 3.1. Отзыв прав на внесение, изменение и удаление данных
-- Права отзываются глобально (*.*), так как выдавались на глобальном уровне
REVOKE INSERT, UPDATE, DELETE ON *.* FROM 'sys_temp'@'localhost';

-- 3.2. Проверка обновления списка прав
SHOW GRANTS FOR 'sys_temp'@'localhost';
```
