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

* удалить контейнер с сервером

![image](https://user-images.githubusercontent.com/40095258/231485372-07fee0b2-7820-472b-9d1c-98bc099cacd3.png)

*удалить получилось только после остановки*

* создать его заново
* подключится снова из контейнера с клиентом к контейнеру с сервером
* проверить, что данные остались на месте

![image](https://user-images.githubusercontent.com/40095258/231486540-3bf990f6-1fe8-442d-bf64-8b34378bde6e.png)

*конечно данные все остались так как мы в контейнер пробросили внешнюю для него папку кластера pg*
![image](https://user-images.githubusercontent.com/40095258/231488939-00b64fd8-1fb0-4f7b-a80e-25f36ca9b176.png)

