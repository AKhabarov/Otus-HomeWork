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
Во второй сессии 5722 две успешно установленные аналогично первой, одна не установлена так как ожидание разблокировки строки от первой транзакции и еще добавляется блокировка типа tuple, так как это вторая транзакция то она успешно установлена.
В третьей сессии 5546 две успешно установленные аналогично первой и одна ожидает установки типа tuple.
В очереди видно что 5722 ждет освобождения строки от первой транзакции, а 5546 ждет освобождения tuple*


## 3. Воспроизведите взаимоблокировку трех транзакций. Можно ли разобраться в ситуации постфактум, изучая журнал сообщений?

* Вначале каждая сессия блокирует отдельную строку:

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/3fb4c27f-e930-4660-ab1a-c38321e8d8b5)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/995fa3aa-541c-4440-91e8-15268398d71d)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/9bb5b763-0417-4d39-9f09-4dd8b961fdc1)

* затем в первой сессии пытаемся сделать апдейт второй строки, во второй - апдейт третьей строки, в третьей сессии - апдейт первой строки:

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/71c946c0-5c32-4ccf-bf09-f110461bf14b)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/7b9bc33c-3d55-4be1-ade8-9d0784f3d409)

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/9ee5c437-3183-4a14-8030-4a55f72dff93)

* Через секунду в третьей сессии получаем deadlock:

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/7483548f-7ad5-456d-abc1-98fe7c397b7c)

* разобраться по журналу можно, там подробно расписано кто кого блокировал, из-за чего образовался дедлок:

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/9cd3b6ce-8de4-4df3-92df-da13e00d81d1)


