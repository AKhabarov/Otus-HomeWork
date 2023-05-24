## 1. Создаем ВМ/докер c ПГ.

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/ce6dce62-22af-4456-a545-00ebfdebfa59)

## 2. Создаем БД, схему и в ней таблицу.

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/212ad8a7-f074-4dee-b15e-5a5c8f8c1ced)

## 3. Заполним таблицы автосгенерированными 100 записями.

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/5f850896-6199-4980-88f4-b53186f497ef)

## 4. Под линукс пользователем Postgres создадим каталог для бэкапов

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/7d53a19d-b0ee-4583-9ce0-799de8242b14)

## 5. Сделаем логический бэкап используя утилиту COPY

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/9f8691fe-539a-463e-9404-21c90e5d8614)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/31661505-7c23-4b5d-a332-55be64f3e99f)

## 6. Восстановим в 2 таблицу данные из бэкапа. 

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/68bcb629-f233-4a5b-b851-33aa88334312)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/dd7f23c6-f701-4d07-b41d-35c0639ba9a1)

## 7. Используя утилиту pg_dump создадим бэкап с оглавлением в кастомном сжатом формате 2 таблиц

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/7b5f6e91-ad9e-4c74-a14c-63e3bb464b28)

## 8. Используя утилиту pg_restore восстановим в новую БД только вторую таблицу!

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/f2d4f407-f5e5-4208-84a6-6aca512391f5)

* перед восстановлением создал новую бд test_restore, добавил в нее схему myschema но почему то не хочет загружаться вторая таблица. Не понимаю что не так, попробовал сотню разных варинатов и отдельно схему выгружал ( -n) и отдельно загружал схему и таблицу, не помогает*



