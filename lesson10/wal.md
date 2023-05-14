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

