# dbt_example
подробное описание - https://github.com/surfalytics/data-projects/blob/main/de-projects/18_dbt_intro/readme.md

1) используем Postgres
2) открываем в dbeaver скрипт dbt_create_schemas.sql, создаем схемы и таблицы
3) вставляем данные в таблицы из файла dbt_insert_data.sql
4) создаем питон-окружение `python3 -m venv venv`, активируем `source venv/bin/activate`
5) устанавливаем dbt: `python -m pip install dbt-core dbt-postgres`
6) устанавливаем pre-commit
7) создаем файл requirements.txt с указанием нужных версий библиотек командой `pip freeze -l > requeriments.txt`
8) `dbt init` - инициализация проекта
9) указываем данные для подключения к БД, в рез-те получаем ссылку на конфиг /Users/nataly/.dbt/profiles.yml
10) все модели - в папке models, описание моделей - в schema.yml
11) автоматически создались две модели (потом папку example можно удалить), проверим, все ли работает, запустив `dbt run` и `dbt test`
12) все запросы можно посмотреть в привычном sql-формате в папках target/compiled/ и target/run/
13) создаем две папки в models по числу слоев: staging и mart. В staging два источника - jaffle_shop и stripe, в mart - итоговая таблица фактов
14) создаем тестовую модель customer_sales (customer_sales.sql) в jaffle_shop/. Не забываем указать в конфиге dbt_project.yml информацию по новой модели staging, НЕ customer_sales (тип материализации и другие параметры)
15) пробуем запустить модели - `dbt run` или конкретную модель `dbt run --select <имя модели>`
16) можем проверить в бобре, создалась ли вьюшка customer_sales
17) в dbt используем source и reference модели не указывая реальные названия таблиц
18) создадим три source-модели в слое staging. Для каждой создаем конфиг (типа _jaffle_shop_sources.yml) и сам файл sql (типа stg_jaffle_shop__customers.sql)
19) добавим документацию и generic-тесты (внутри модели для конкретной колонки) для трех source-моделей (типа stg_jaffle_shop__customers.yml)
20) таким образом, у каждой модели есть два файла с одинаковым названием, но разными расширениями: sql и yml
21) есть еще singular-тесты (sql-запросы, размещаются в папке tests)
22) запускаем модели по тегу staging: `dbt run --select tag:staging`
23) добавим pre-commit файл в корень репо для проверки кода до того, как запушим (другой вариант - sqlfluff).
24) активируем командой `pre-commit install`





