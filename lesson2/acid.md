* поставить PostgreSQL
* зайти вторым ssh (вторая сессия)
* запустить везде psql из под пользователя postgres:
![image](https://user-images.githubusercontent.com/40095258/230610252-b7615df1-530b-47f2-b949-eacc001f69e2.png)

* выключить auto commit:

![image](https://user-images.githubusercontent.com/40095258/230729007-2930d1f0-ad81-4e91-8b11-dee9f9f89fbf.png)
![image](https://user-images.githubusercontent.com/40095258/230728343-bb100937-e745-497c-b640-2e0d0d6dca9b.png)

* сделать в первой сессии новую таблицу и наполнить ее данными:

![image](https://user-images.githubusercontent.com/40095258/230728966-7ab38724-8fb7-473b-933e-69379820564a.png)

* посмотреть текущий уровень изоляции:

![image](https://user-images.githubusercontent.com/40095258/230729077-e77fc655-8439-4749-9abd-7e5da4c447a1.png)

* начать новую транзакцию в обоих сессиях с дефолтным (не меняя) уровнем изоляции:

![image](https://user-images.githubusercontent.com/40095258/230729212-de3c67da-d8f5-44c4-8b3b-afa72082dd4c.png)
![image](https://user-images.githubusercontent.com/40095258/230729223-d3a3d0ee-70a2-4e03-b9a8-be2becd4a783.png)

* в первой сессии добавить новую запись:

![image](https://user-images.githubusercontent.com/40095258/230729274-4cc466c0-7f3e-4cf1-807f-931f43b6b9c9.png)

* сделать select * from persons во второй сессии:

![image](https://user-images.githubusercontent.com/40095258/230729333-91f1f03d-2263-439b-bfc7-c64760a7ded5.png)

* видите ли вы новую запись и если да то почему?
  * Не видим, потому что в read commited нет грязного чтения, а транзакция первой сессии не завершена.
  
* завершить первую транзакцию - commit;

![image](https://user-images.githubusercontent.com/40095258/230729565-e6b8b702-815e-4b95-951a-9cafe8bf89b0.png)

* сделать select * from persons во второй сессии

![image](https://user-images.githubusercontent.com/40095258/230729641-1dc29ac0-fe44-4fe3-b068-31a95dcb6d2d.png)

* видите ли вы новую запись и если да то почему?
  * видим, потому что теперь транзакция завершилась и грязного чтения уже нет.

* начать новые но уже repeatable read транзации

![image](https://user-images.githubusercontent.com/40095258/230729942-79b512b4-67d6-41b2-9f25-f0e4438729da.png)
![image](https://user-images.githubusercontent.com/40095258/230729961-e68c5179-d3d1-410a-a054-70ef7ef2bcbc.png)

* в первой сессии добавить новую запись
![image](https://user-images.githubusercontent.com/40095258/230730052-1ab6a300-c47b-44e2-9f60-825c7e7697d2.png)

* сделать select * from persons во второй сессии

![image](https://user-images.githubusercontent.com/40095258/230730167-d0906edb-3b67-4c26-bdad-90f8153c9e02.png)

* видите ли вы новую запись и если да то почему?
  * не видим, грязное чтение

* завершить первую транзакцию:

![image](https://user-images.githubusercontent.com/40095258/230730320-835e2892-d7de-4fc5-9378-85c2e9d475a6.png)

* сделать select * from persons во второй сессии:

![image](https://user-images.githubusercontent.com/40095258/230730379-8095e201-1bcf-4790-a54d-dc48a796c442.png)

* видите ли вы новую запись и если да то почему?
  * не видим, потому что на этом уровне нет проблемы неповторяемого чтения в одной транзакции




