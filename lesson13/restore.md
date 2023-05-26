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

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/baf95406-4b9c-4b7d-a90c-2630e4b07b47)

## 8. Используя утилиту pg_restore восстановим в новую БД только вторую таблицу!

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/2c67251f-d682-4c24-8332-b36b2d5824cc)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/20d85f58-f47d-403a-8cab-4a6c946265d1)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/558f04e7-d9fd-47ae-9ee9-77a9fe8ab0f7)

*в новую базу test_restore загрузилась только вторая таблица*


