
# Основное задание

* Создать инстанс ВМ с 2 ядрами и 4 Гб ОЗУ и SSD 10GB
* Установить на него PostgreSQL 15 с дефолтными настройками

![image](https://user-images.githubusercontent.com/40095258/235343637-d3ae8fb3-e9ba-461d-80cf-a28b6eb8f9b8.png)

* Создать БД для тестов: выполнить pgbench -i postgres

![image](https://user-images.githubusercontent.com/40095258/235344028-c503a192-2333-4f77-a006-8e17de247e6b.png)

![image](https://user-images.githubusercontent.com/40095258/235344195-d225cb53-5ce1-40d8-8cd9-e8ac8f091b30.png)

* Запустить pgbench -c8 -P 6 -T 60 -U postgres postgres

![image](https://user-images.githubusercontent.com/40095258/235344276-079be3b0-3cd0-4599-b812-5686bebc67b6.png)

* Применить параметры настройки PostgreSQL из прикрепленного к материалам занятия файла

![image](https://user-images.githubusercontent.com/40095258/235344515-2a0a7804-785d-430f-b392-5a063d12179b.png)

![image](https://user-images.githubusercontent.com/40095258/235345471-9d0556d8-3bdd-4306-9d3d-e0037bca5046.png)

* Протестировать заново

![image](https://user-images.githubusercontent.com/40095258/235345624-4baf3022-602b-4ef3-b39a-68b692ef81aa.png)
