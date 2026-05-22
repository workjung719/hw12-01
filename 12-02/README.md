# Домашнее задание к занятию "`Работа с данными (DDL/DML)`" -`Лазебный Кирилл`

---

### Задание 1

`Выполнил запрос на получение списка пользователей в базе данных.`

<img width="1920" height="1031" alt="1" src="https://github.com/user-attachments/assets/6dd0f020-34a5-4f92-a683-540d9494f44e" />


`Выполнил запрос на получение списка прав для пользователя sys_temp.`

<img width="1920" height="1031" alt="2" src="https://github.com/user-attachments/assets/f8269f31-8711-4ae8-aca0-3ecd8fe49386" />


`Скачал и восстановил дамп базы данных и сформировал ER-диаграмму.`

<img width="1920" height="1031" alt="3" src="https://github.com/user-attachments/assets/3c5e6fc8-5fad-43a1-81ab-86042a53055a" />

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
Название таблицы | Название первичного ключа
actor	           | actor_id
address	         | address_id
category	       | category_id
city	           | city_id
country	         | country_id
customer	       | customer_id
film	           | film_id
film_actor	     | actor_id
film_actor	     | film_id
film_category	   | film_id
film_category	   | category_id
film_text	       | film_id
inventory	       | inventory_id
language	       | language_id
payment	         | payment_id
rental	         | rental_id
staff	           | staff_id
store	           | store_id
```


<img width="1920" height="1031" alt="4" src="https://github.com/user-attachments/assets/04bb15ae-fa8b-4422-aa7b-49df591c5a88" />

---

### Задание 3

`Выполнил запрос на получение списка прав для пользователя sys_temp после удаления у пользователя следующих прав - (INSERT, UPDATE, DELETE).`

<img width="1920" height="1020" alt="5" src="https://github.com/user-attachments/assets/f8cdb383-bb8d-414d-ac3e-ff7a0a7f90f3" />


<img width="1920" height="1031" alt="6" src="https://github.com/user-attachments/assets/c04b18ed-fdfc-44d9-af41-db068ee9ae7b" />

#### Простыня SQL-запросов

```SQL
-- 3.1. Отзыв прав на внесение, изменение и удаление данных
-- Права отзываются глобально (*.*), так как выдавались на глобальном уровне
REVOKE INSERT, UPDATE, DELETE ON *.* FROM 'sys_temp'@'localhost';

-- 3.2. Проверка обновления списка прав
SHOW GRANTS FOR 'sys_temp'@'localhost';
```

