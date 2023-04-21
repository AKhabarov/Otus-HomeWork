
* создайте виртуальную машину c Ubuntu 20.04 LTS в GCE типа e2-medium в default VPC в любом регионе и
зоне, например us-central1-a
  * поставьте на нее PostgreSQL через sudo apt
  * проверьте что кластер запущен через sudo -u postgres pg_lsclusters

![image](https://user-images.githubusercontent.com/40095258/233594466-6b4ac00c-e5a9-48b4-bdb7-fa7dfa925779.png)

* зайдите из под пользователя postgres в psql и сделайте произвольную таблицу с произвольным
содержимым

![image](https://user-images.githubusercontent.com/40095258/233596464-6de1c6e8-6020-4079-8f0e-e999061ad919.png)

