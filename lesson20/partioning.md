# Секционировать большую таблицу из демо базы flights

## 1. разворачиваем демо-базу

psql -f /mnt/demo-medium-20170815.sql -U postgres

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/c5d37765-38d9-4572-b031-95d98fa17b0e)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/203d2be9-4efa-4ba9-89b7-4afbe44389cc)


## 2. Секционируем таблицу ticket_flights по хэшу

создаем новую таблицу с аналогичной структурой, с разбиением по колонке flight_id:

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/73e70b89-ee9a-44eb-b640-3e06c9c7c897)

создаем секции (на втором шаге ошибка, неправильно указан модуль, сделал этот шаг в конце):

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/94783663-40ef-4da3-a4d3-e559056111e3)

копируем записи из первоначальной таблицы в новую:

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/f3c231cd-3d61-41d4-88a8-2864f0e026f5)

проверяем распределение (в каждой секции получилось примерно по 460 тыс. строк):

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/9e166b6d-083e-43e8-a23a-28bb49675138)
