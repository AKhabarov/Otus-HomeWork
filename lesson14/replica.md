
### На 1 ВМ создаем таблицы test для записи, test2 для запросов на чтение.
### Создаем публикацию таблицы test и подписываемся на публикацию таблицы test2 с ВМ №2.
### На 2 ВМ создаем таблицы test2 для записи, test для запросов на чтение.
### Создаем публикацию таблицы test2 и подписываемся на публикацию таблицы test с ВМ №1.

1 ВМ:

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/1568dd10-f607-48f1-978c-a90303ffd7df)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/28be78bc-48b0-499e-a210-eabc15e0bb5a)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/14441af3-95ee-4a2b-a4cf-17c7670ba41a)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/495fdb5d-e09a-4796-a9e0-b6ec23b7b1e7)

создаем публикацию таблицы test:

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/4019f1b8-0ee4-461e-8c21-6c6a5333c655)

2 ВМ:

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/bf61884b-64ba-4755-8e8a-77298c7b17e2)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/a6affd3b-5d0b-4a0a-bacc-37b316135cef)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/78334d4e-2dbc-43f2-8634-6b2aa7f43f84)

создаем публикацию таблицы test2:

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/ef9520f3-1b79-4301-9023-bc051b946c00)

теперь можно подписываться на обоих ВМ:

1 ВМ:

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/f7097067-f64e-4db8-b077-9a4f546b9f98)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/1c9d1f1f-3489-4ee3-90a3-2ca921e83d56)

2 ВМ:

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/a21eeab9-19a5-4762-96d5-e649d0584efa)

(вначале выдавало ошибку, пришлось увеличить max_wal_senders на первой ВМ)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/0b3d5077-1ccd-4925-abf2-a8dd12599536)

после этого подписка создалась:

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/1f549b5c-0c91-4201-a676-bf7f6dec632f)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/82d3cb3e-190c-4876-ba7b-a12b042fbc35)


### 3 ВМ использовать как реплику для чтения и бэкапов (подписаться на таблицы из ВМ №1 и №2 )

3 ВМ:

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/8ded2602-51df-4a21-9341-1d7ee3d58815)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/5bfb7e92-02aa-465b-92cf-e20eae51be82)

делаем подписку на таблицу test на ВМ1:

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/eb788ecd-4c8d-4e89-935e-35b68740057b)

а теперь на таблицу test2 на ВМ2:

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/be2a5e68-12f2-4230-bb1c-d1bb5995d8e7)
