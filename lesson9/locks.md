## 1.  Настройте сервер так, чтобы в журнал сообщений сбрасывалась информация о блокировках, удерживаемых более 200 миллисекунд. Воспроизведите ситуацию, при которой в журнале появятся такие сообщения.

 ![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/72ebef50-9d0d-42a1-a357-b2d8ec72e6ee)
 
 * 1 сессия
  
 ![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/61101d72-71ef-48db-b024-1da0cf78d64f)

* 2 сессия
 
![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/47fc3b36-740d-46c5-b9d4-e796896ae866)

* журнал

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/2233d741-a055-4c50-9008-9b383aac0a80)

## 2. Смоделируйте ситуацию обновления одной и той же строки тремя командами UPDATE в разных сеансах. Изучите возникшие блокировки в представлении pg_locks и убедитесь, что все они понятны. Пришлите список блокировок и объясните, что значит каждая.

* 1 сессия

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/42c43948-933d-45af-beea-23c739ea70a1)

* 2 сессия

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/55264206-fc26-4ece-8842-8aebd531c1ae)

* 3 сессия

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/aee34353-7209-4d1a-a7d0-1d414b9dcd8a)

* блокировки:

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/3b7468b5-2a7d-428c-8f0b-e3d583faf335)

* очередь ожиданий:

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/efea7a38-611a-4d1c-9794-079b4c470291)

*В первой сессии 5203 две успешно установленные блокировки - на таблицу и на номер транзакции.
Во второй сессии 5722 две успешно установленные аналогично первой, одна не установлена так как ожидание разблокировки строки от первой транзакции и еще добавляется блокировка типа tuple, так как это вторая транзакция то она успешно установлена
В третьей сессии 5546 две успешно установленные аналогично первой и одна ожидает установки типа tuple*

