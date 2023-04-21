
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







