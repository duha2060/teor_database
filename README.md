# Домашнее задание к занятию "`Базы данных и их типы`" - `Максимов Андрей Дмитриевич`


### Инструкция по выполнению домашнего задания

   1. Сделайте `fork` данного репозитория к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/git-hw или  https://github.com/имя-вашего-репозитория/7-1-ansible-hw).
   2. Выполните клонирование данного репозитория к себе на ПК с помощью команды `git clone`.
   3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
      - впишите вверху название занятия и вашу фамилию и имя
      - в каждом задании добавьте решение в требуемом виде (текст/код/скриншоты/ссылка)
      - для корректного добавления скриншотов воспользуйтесь [инструкцией "Как вставить скриншот в шаблон с решением](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md)
      - при оформлении используйте возможности языка разметки md (коротко об этом можно посмотреть в [инструкции  по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md))
   4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`);
   5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
   6. Любые вопросы по выполнению заданий спрашивайте в чате учебной группы и/или в разделе “Вопросы по заданию” в личном кабинете.
   
Желаем успехов в выполнении домашнего задания!
   
### Дополнительные материалы, которые могут быть полезны для выполнения задания

1. [Руководство по оформлению Markdown файлов](https://gist.github.com/Jekins/2bf2d0638163f1294637#Code)

---

### Задание 1

Задание 1. СУБД
Кейс
Крупная строительная компания, которая также занимается проектированием и девелопментом, решила создать правильную архитектуру для работы с данными. Ниже представлены задачи, которые необходимо решить для каждой предметной области.

Какие типы СУБД, на ваш взгляд, лучше всего подойдут для решения этих задач и почему?

1.1. Бюджетирование проектов с дальнейшим формированием финансовых аналитических отчётов и прогнозирования рисков. СУБД должна гарантировать целостность и чёткую структуру данных.
Реляционные базы данных, или базы данных SQL Основная особенность — надежность и неизменяемость данных, низкий риск потери информации.

1.1.* Хеширование стало занимать длительно время, какое API можно использовать для ускорения работы?

СУБД типа ключ-значение Чаще всего такие СУБД используют для кэширования, т.к. они очень быстро работают, а это и не сложно, когда есть уникальный ключ, и запрос возвращает только одно значение. подойдут Redis, Memcached. md5 - это быстрый хэш. То есть он предназначен для использования больших объемов данных и вывода хэша очень, очень быстро.

1.2. Под каждый девелоперский проект создаётся отдельный лендинг, и все данные по лидам стекаются в CRM к маркетологам и менеджерам по продажам. Какой тип СУБД лучше использовать для лендингов и для CRM? СУБД должны быть гибкими и быстрыми.

MySQL Данная СУБД работает с реляционными данными и имеет свободное программное обеспечение , СУБД заслужено считается одной из самых гибких и быстродействующих, поэтому ее предлагают использовать для проектов малых и средних объемов. 

1.2.* Можно ли эту задачу закрыть одной СУБД? И если да, то какой именно СУБД и какой реализацией?
Можно PostgreSQL с jsonb

1.3. Отдел контроля качества решил создать базу по корпоративным нормам и правилам, обучающему материалу и так далее, сформированную согласно структуре компании. СУБД должна иметь простую и понятную структуру.
MongoDB рассчитана на работу с данными иерархической структуры. По сути, это хранилище документов без использования схематичного или табличного форматов, поэтому ее еще называют документоориентированной. MongoDB базы данных подключаются к приложениям через драйверы баз данных. Несколько типов данных обрабатываются одновременно и для этой цели используется внутренний кэш. Плюсы MongoDB 1) Простой доступ к данным, их хранение, ввод и извлечение. Одним из преимуществ MongoDB, вытекающих из его природы NoSQL, является быстрая и простая обработка данных. СУБД MongoDB рекомендуют использовать там, где отсутствуют потребности в сложных выборках.

1.3.* Можно ли под эту задачу использовать уже существующую СУБД из задач выше и если да, то как лучше это реализовать?

1.4. Департамент логистики нуждается в решении задач по быстрому формированию маршрутов доставки материалов по объектам и распределению курьеров по маршрутам с доставкой документов. СУБД должна уметь быстро работать со связями.
Графовые Особые СУБД, предназначенные для хранения информации, связанной с графами (узлы, вершины, связи между узлами). Хорошо подходят для социальных сетей, где требуется хранить связи между пользователями по разным критериям.

1.4.* Можно ли к этой СУБД подключить отдел закупок или для них лучше сформировать свою СУБД в связке с СУБД логистов?

1.5.* Можно ли все перечисленные выше задачи решить, используя одну СУБД? Если да, то какую именно?

---

### Задание 2

2.1. Пользователь пополняет баланс счёта телефона, распишите пошагово, какие действия должны произойти для того, чтобы транзакция завершилась успешно. Ориентируйтесь на шесть действий.
```
1. Проверить баланс пользователя
2. Найти второго пользователя, если не найден транзакция не завершится.
3. Уменьшить баланс первого пользователя на 100 единиц, если сумма платежа<баланса, иначе транзакция не завершится.
4. Увеличить баланс второго пользователя на 100 единиц.
5. Увеличить значение, когда оканчивается тариф  у первого пользователя на один месяц.
```

2.1.* Какие действия должны произойти, если пополнение счёта телефона происходило бы через автоплатёж?
---

### Задание 3
3.1. Напишите пять преимуществ SQL-систем по отношению к NoSQL.

1. Обладают жесткой структурой, а это позволяет переносить одну и ту же БД на разные СУБД
2. Данные хранятся структурированно.
3. Обеспечивают целостность данных.
4. Структура не подвержена частым изменением.
5. Если организация не находится в стадии экспоненциального роста, вероятно, не найдётся убедительных причин использовать БД, 
которая позволяет достаточно вольно обращаться с типами данных и нацелена на обработку огромных объёмов информации.

3.1.* Какие, на ваш взгляд, преимущества у NewSQL систем перед SQL и NoSQL.

### Задание 4
Необходимо производить большое количество вычислений при работе с огромным количеством данных, под эту задачу выделено 1000 машин.
На основе какого критерия будете выбирать тип СУБД и какая модель распределённых вычислений здесь справится лучше всего и почему?
Приведите ответ в свободной форме.
```
Лучшее решение для этого Hadoop, она состоит из таких компонентов как:
1.Hadoop Distributed File System (HDFS) – распределённая файловая система, позволяющая хранить информацию практически неограниченного объёма.
2.Hadoop YARN – фреймворк для управления ресурсами кластера и менеджмента задач, в том числе включает фреймворк MapReduce.
То есть можно хранить неограниченное кол-во данных и управлять кластером.
Также существует большое количество проектов непосредственно связанных с Hadoop, но не входящих в Hadoop core:
Hive – инструмент для SQL-like запросов над большими данными (превращает SQL-запросы в серию MapReduce–задач);
Pig – язык программирования для анализа данных на высоком уровне. Одна строчка кода на этом языке может превратиться в последовательность MapReduce-задач;
Hbase – колоночная база данных, реализующая парадигму BigTable;
Cassandra – высокопроизводительная распределенная key-value база данных;
ZooKeeper – сервис для распределённого хранения конфигурации и синхронизации изменений этой конфигурации;
Mahout – библиотека и движок машинного обучения на больших данных.
Можно подстроить систему под свои нужды.
Данное решение широко используется в поисковых системах типа Google Yahoo и тд, для быстрой обработки графических данных, 
хранение и сортировка огромных объемов данных, и разбор содержимого чрезвычайно больших файлов.
```



