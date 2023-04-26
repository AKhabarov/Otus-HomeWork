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


