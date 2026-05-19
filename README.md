# Домашнее задание к занятию "Базы данных" - Лазебный Кирилл

### Инструкция по выполнению домашнего задания

1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
   - впишите вверху название занятия и вашу фамилию и имя
   - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
   - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
   - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.

---

### Задание 1

Описываем таблицы из которых состоит база данных.

В отправленном заказчиком Excel файле можно описать следующие таблицы:

```SQL
CREATE TABLE positions (
id SERIAL PRIMARY KEY,
title VARCHAR(100) NOT NULL
);

CREATE TABLE department_types (
id SERIAL PRIMARY KEY,
type VARCHAR(50) NOT NULL
);

CREATE TABLE branch (
id SERIAL PRIMARY KEY,
address VARCHAR(150) NOT NULL
);

CREATE TABLE projects (
id SERIAL PRIMARY KEY,
project VARCHAR(100) NOT NULL
);

CREATE TABLE departments (
id SERIAL PRIMARY KEY,
name VARCHAR(150) NOT NULL,
type_id INTEGER NOT NULL,
FOREIGN KEY (type_id) REFERENCES department_types(id)
);

CREATE TABLE employees (
id SERIAL PRIMARY KEY,
full_name VARCHAR(150) NOT NULL,
salary NUMERIC(10, 2) NOT NULL,
hire_date DATE NOT NULL,
position_id INTEGER NOT NULL,
department_id INTEGER NOT NULL,
branch_id INTEGER NOT NULL,
FOREIGN KEY (position_id) REFERENCES positions(id),
FOREIGN KEY (department_id) REFERENCES departments(id),
FOREIGN KEY (branch_id) REFERENCES branch(id)
);

CREATE TABLE employee_projects (
employee_id INTEGER NOT NULL,
project_id INTEGER NOT NULL,
PRIMARY KEY (employee_id, project_id),
FOREIGN KEY (employee_id) REFERENCES employees(id),
FOREIGN KEY (project_id) REFERENCES projects(id)
);
```

![Схема БД](D:\Developer\2_Playground\netology%20homework\SQL\1.%20Базы%20данных\hw12-01\hw_image\schema.png)

---

### Задание 2

База данных успешно развернута локально в PostgreSQL. SQL-скрипт выполнен, таблицы и связи созданы.

![dbeaver_schema.png](D:\Developer\2_Playground\netology%20homework\SQL\1.%20Базы%20данных\hw12-01\hw_image\dbeaver_schema.png)



---
