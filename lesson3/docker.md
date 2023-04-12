* создать ВМ с Ubuntu 20.04/22.04 или развернуть докер любым удобным способом
* поставить на нем Docker Engine

![image](https://user-images.githubusercontent.com/40095258/231465293-ea0546ae-4309-435f-ac18-c2b426b6f05d.png)

* сделать каталог /var/lib/postgres

![image](https://user-images.githubusercontent.com/40095258/231465788-c35c54b7-8acb-45e6-9326-476937a97273.png)

* развернуть контейнер с PostgreSQL 15 смонтировав в него /var/lib/postgresql

![image](https://user-images.githubusercontent.com/40095258/231467001-5d4f617a-e349-4f8c-923e-924f4274a810.png)

* развернуть контейнер с клиентом postgres

![image](https://user-images.githubusercontent.com/40095258/231467650-f9710e57-ee83-403b-a6f8-0e163fc4c000.png)

* подключится из контейнера с клиентом к контейнеру с сервером и сделать таблицу с парой строк

![image](https://user-images.githubusercontent.com/40095258/231473700-dcd1a470-12b4-43a0-9e46-56be4f12b84b.png)

*понял что создал таблицу testtable не в той базе и создал заново*

![image](https://user-images.githubusercontent.com/40095258/231474090-9161689e-0660-4414-a6e7-0e1236ec2759.png)

* подключится к контейнеру с сервером с ноутбука/компьютера извне инстансов GCP/ЯО/места установки докера

![image](https://user-images.githubusercontent.com/40095258/231483577-b1e03207-fb9a-4e53-bdf5-4256405a4064.png)

*подключился с продуктивного рабочего сервера на котором был установлен postgresql. Вначле не получалось запустить команду psql, потом перешел в каталог /opt/pgpro/1c-14/bin и оттуда уже смог запустить*

