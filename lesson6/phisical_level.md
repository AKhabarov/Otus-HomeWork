
# Основное задание 
* создайте виртуальную машину c Ubuntu 20.04 LTS в GCE типа e2-medium в default VPC в любом регионе и
зоне, например us-central1-a
  * поставьте на нее PostgreSQL через sudo apt
  * проверьте что кластер запущен через sudo -u postgres pg_lsclusters

![image](https://user-images.githubusercontent.com/40095258/233594466-6b4ac00c-e5a9-48b4-bdb7-fa7dfa925779.png)

* зайдите из под пользователя postgres в psql и сделайте произвольную таблицу с произвольным
содержимым

![image](https://user-images.githubusercontent.com/40095258/233596464-6de1c6e8-6020-4079-8f0e-e999061ad919.png)

* остановите postgres например через sudo -u postgres pg_ctlcluster 14 main stop

![image](https://user-images.githubusercontent.com/40095258/233598674-9c08cc72-8c53-4a13-ac38-7777f7404ea4.png)

* создайте новый standard persistent диск GKE через Compute Engine -> Disks в том же регионе и зоне что
GCE инстанс размером например 10GB
  * добавьте свеже-созданный диск к виртуальной машине - надо зайти в режим ее редактирования и
дальше выбрать пункт attach existing disk

![image](https://user-images.githubusercontent.com/40095258/233601321-a4e8a50f-98ea-4f68-b13f-23e0eb3096b8.png)

* проинициализируйте диск согласно инструкции и подмонтировать файловую систему

![image](https://user-images.githubusercontent.com/40095258/233606454-66b9b367-ca78-4d86-802f-6dbd30799ec5.png)

* перезагрузите инстанс и убедитесь, что диск остается примонтированным

![image](https://user-images.githubusercontent.com/40095258/233607567-55279b1f-60ea-49d0-a5f9-5fe6417952a7.png)

* сделайте пользователя postgres владельцем /mnt/data

![image](https://user-images.githubusercontent.com/40095258/233607988-39ae5e1c-cb13-452e-a707-33a9722e7cd7.png)

* перенесите содержимое /var/lib/postgres/14 в /mnt/data

![image](https://user-images.githubusercontent.com/40095258/233608789-9c5f99db-c549-4fcb-8826-10efa78c543e.png)

* попытайтесь запустить кластер

![image](https://user-images.githubusercontent.com/40095258/233608982-b4f3affd-d3f4-4a5b-b6c7-11a1c3c0d0b9.png)

*не получилось потому что каталог кластера мы перенесли в /mnt/data*

* найти конфигурационный параметр в файлах расположенных в /etc/postgresql/14/main
который надо поменять и поменяйте его

![image](https://user-images.githubusercontent.com/40095258/233609984-9cdc9dea-d10d-4606-a09b-519244e984cd.png)

*поменяли параметр data_directory*

попытайтесь запустить кластер

![image](https://user-images.githubusercontent.com/40095258/233611283-eeda9e33-d356-40bd-a602-fcc62addb1a6.png)

*теперь все в порядке*

* зайдите через через psql и проверьте содержимое ранее созданной таблицы

![image](https://user-images.githubusercontent.com/40095258/233611701-46b727b5-3594-4a0e-86b1-ae0e565aa34c.png)

 
# Задание с *

* не удаляя существующий GCE инстанс сделайте новый, поставьте на него
PostgreSQL
![image](https://user-images.githubusercontent.com/40095258/233618173-c3ad8f68-78da-45d2-9d66-a0df9195a7c9.png)
![image](https://user-images.githubusercontent.com/40095258/233619666-c2a9d44f-6137-4204-b411-8d33ab493bfd.png)

* удалите файлы с данными из /var/lib/postgres

![image](https://user-images.githubusercontent.com/40095258/233628128-c67e8f0a-3877-4380-bcfb-507eb3859cd6.png)

* перемонтируйте внешний диск который
сделали ранее от первой виртуальной машины ко второй и запустите PostgreSQL на второй машине так
чтобы он работал с данными на внешнем диске, расскажите как вы это сделали и что в итоге получилось

![image](https://user-images.githubusercontent.com/40095258/233630554-0f408909-1c60-4da6-ae35-065e6d9c0802.png)

*так как файловая система на внешнем диске уже была создана, то осталось только примонтировать к вновь созданной папке*

![image](https://user-images.githubusercontent.com/40095258/233630920-b9799629-3ef2-4832-990f-4b6431f2091e.png)

*затем редактируем параметр data_directory в конфигурационном файле и запускаем постгрес, убеждаемся что тестовая база сохранилась. Бинго*




