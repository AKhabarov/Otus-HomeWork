### 1 создайте новый кластер PostgresSQL 14
### 2 зайдите в созданный кластер под пользователем postgres
### 3 создайте новую базу данных testdb

![image](https://user-images.githubusercontent.com/40095258/234668653-46736731-ff29-49ee-b7e5-951c50d93b3e.png)

![image](https://user-images.githubusercontent.com/40095258/234668849-810cee66-c92c-411f-9f6e-0410a7cde23c.png)

### 4 зайдите в созданную базу данных под пользователем postgres

![image](https://user-images.githubusercontent.com/40095258/234669088-7f98d108-80ba-489e-a290-28ea3a20af4b.png)

### 5 создайте новую схему testnm

![image](https://user-images.githubusercontent.com/40095258/234670134-ea1aa9ce-0302-4fe8-930a-406a96c26881.png)

### 6 создайте новую таблицу t1 с одной колонкой c1 типа integer
### 7 вставьте строку со значением c1=1

![image](https://user-images.githubusercontent.com/40095258/234670899-505df793-9f51-4291-ac30-f434aba38359.png)

### 8 создайте новую роль readonly

![image](https://user-images.githubusercontent.com/40095258/234672101-a0d912f2-0bd2-4ee7-9b4c-ccf544d15f06.png)

### 9 дайте новой роли право на подключение к базе данных testdb

![image](https://user-images.githubusercontent.com/40095258/234675418-2f3cc71a-81c6-4bda-b0c0-ff299a232855.png)

### 10 дайте новой роли право на использование схемы testnm

![image](https://user-images.githubusercontent.com/40095258/234678590-612bf1b6-1774-4688-89d1-7caf99585548.png)

### 11 дайте новой роли право на select для всех таблиц схемы testnm

![image](https://user-images.githubusercontent.com/40095258/234678849-e20b9a3a-e6bb-4a8f-b634-42f010ce9e2c.png)

### 12 создайте пользователя testread с паролем test123

![image](https://user-images.githubusercontent.com/40095258/234680132-f9ca833f-3cf1-4665-81dc-7c34513079dc.png)

### 13 дайте роль readonly пользователю testread

![image](https://user-images.githubusercontent.com/40095258/234682254-0d65c465-f8ca-40b3-a76f-726b719420a1.png)

### 14 зайдите под пользователем testread в базу данных testdb

![image](https://user-images.githubusercontent.com/40095258/234686799-11b61496-ccad-4366-95bf-0a189a7e5599.png)

### 15 сделайте select * from t1;

![image](https://user-images.githubusercontent.com/40095258/234687016-85d1358e-6ac8-4247-9945-ff73f5f24a1a.png)

* так получилось потому что таблица t1 создалась в схеме public, а права мы дали на схему testnm

![image](https://user-images.githubusercontent.com/40095258/234687581-9815aeff-568e-471f-a939-937191ca981d.png)

### 22 вернитесь в базу данных testdb под пользователем postgres

![image](https://user-images.githubusercontent.com/40095258/234688215-d5f6c807-d16a-4768-8637-ba44de023198.png)

### 23 удалите таблицу t1
### 24 создайте ее заново но уже с явным указанием имени схемы testnm
### 25 вставьте строку со значением c1=1

![image](https://user-images.githubusercontent.com/40095258/234689274-f63ea443-1312-4313-850a-7acb9ebf2ea1.png)

### 26 зайдите под пользователем testread в базу данных testdb
### 27 сделайте select * from testnm.t1;

![image](https://user-images.githubusercontent.com/40095258/234690072-9f1e04b5-21c2-47f4-a8bf-9175f2ed7248.png)

* 28 получилось?
* 29 есть идеи почему? если нет - смотрите шпаргалку
* потому что у таблицы t1 владелец postgres

![image](https://user-images.githubusercontent.com/40095258/234692848-af69ee74-a5e2-4792-b02f-7a3ccd1cb5cd.png)

* 30 как сделать так чтобы такое больше не повторялось? если нет идей - смотрите шпаргалку

![image](https://user-images.githubusercontent.com/40095258/234693834-a038d68e-1574-4f27-820f-be2550f6982f.png)

### 31 сделайте select * from testnm.t1;

![image](https://user-images.githubusercontent.com/40095258/234694022-3a3bd894-a3a9-4f8b-9aa2-b70c8c4142f8.png)

### 34 теперь попробуйте выполнить команду create table t2(c1 integer); insert into t2 values (2);

![image](https://user-images.githubusercontent.com/40095258/234694544-4fba38ed-a671-454f-9764-c6f06782db33.png)

### 35 а как так? нам же никто прав на создание таблиц и insert в них под ролью readonly?

* потому что мы создали таблицу в схеме public, а на эту схему права по умолчанию есть у всех ролей.

### 36 есть идеи как убрать эти права?

![image](https://user-images.githubusercontent.com/40095258/234697895-53a14113-c62b-481a-9695-0510cf0bfe6e.png)

* первой командой убрали все права у пользователя, второй командой добавили на чтение

### 38 теперь попробуйте выполнить команду create table t3(c1 integer); insert into t2 values (2);

* все равно права на создание таблиц в public остались, после этого поискал в интернете, оказывается надо еще выполнить команду 
* REVOKE CREATE ON SCHEMA public FROM PUBLIC; - так как роль PUBLIC неявно наследуется всеми ролями. После этого все получилось:

![image](https://user-images.githubusercontent.com/40095258/234704226-1df524a6-c121-475c-b52a-3eeb6223a548.png)

![image](https://user-images.githubusercontent.com/40095258/234704810-9f8ba8e0-e62a-4cfd-8c26-8fb17d69d54d.png)




