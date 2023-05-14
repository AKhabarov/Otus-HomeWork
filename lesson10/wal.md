### 1. Настройте выполнение контрольной точки раз в 30 секунд.

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/8eefeea6-1a72-4313-997a-4350fbf97816)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/ff08cc7a-4add-4356-9f04-cae451275d3e)

### 2. 10 минут c помощью утилиты pgbench подавайте нагрузку.

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/a4270b02-913a-496d-8943-a4698f8c7ef1)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/766431cb-0adf-4223-9123-2c4ee56c25c3)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/a979890a-b4fd-4ff0-b256-141b649ea211)

### 3. Измерьте, какой объем журнальных файлов был сгенерирован за это время. Оцените, какой объем приходится в среднем на одну контрольную точку.

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/ec6c41d9-777c-429c-9e84-3b0d1bc3c6bc)

*журнал вырос до 64 Мб, значит на одну контрольную точку приходится в среднем 3,2 Мб*

### 4. Проверьте данные статистики: все ли контрольные точки выполнялись точно по расписанию. Почему так произошло?

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/cc892105-38b5-41c7-8128-2914e025f926)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/a7eb8c40-6516-466a-9e6c-5c52ea3d9035)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/786870fc-dc56-44df-a55d-1b2d47801c9f)

*по статистике все контрольные точки выполнились по расписанию. Так как мы поставили очень маленький таймаут 30 секунд между контрольными точками, то принудительных вызовов контрльных точек не возникает*

### 5. Сравните tps в синхронном/асинхронном режиме утилитой pgbench. Объясните полученный результат.

* Синхронный tps=520:

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/c35e218b-b876-4352-9515-99a903b56189)

* асинхронный tps=4711 (synchronous_commit = off)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/684c3647-7e53-4055-a506-44699e03e404)

Как и следовало ожидать асинхронный режим производительней более чем в 9 раз. Это объясняется тем, что транзакции считаются завершенными еще до их записи в журнал wal на диск.

### 6. Создайте новый кластер с включенной контрольной суммой страниц. Создайте таблицу. Вставьте несколько значений. Выключите кластер. Измените пару байт в таблице. Включите кластер и сделайте выборку из таблицы. Что и почему произошло? как проигнорировать ошибку и продолжить работу?

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/70003de6-2814-4f13-ac83-be90e0133e46)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/dcb4659d-8059-418e-b9a6-0187b5a57113)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/f1c865a5-e74f-4628-909b-5bf5bff369c4)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/55911df9-bef9-4137-b7db-9aeaabccfcf8)

