# Базовый SQL

В проекте нужно проанализировать данные о фондах и инвестициях и написать запросы к базе.

## Знакомство с базой данных

В используемых данных, упоминаются сервисы и компании, запрещённые в РФ.

База данных хранит информацию о венчурных фондах и инвестициях в компании-стартапы. Эта база данных основана на датасете [Startup Investments](https://www.kaggle.com/justinas/startup-investments), опубликованном на популярной платформе для соревнований по исследованию данных Kaggle. 

![ER-диаграмма БД](er_diagramm.png "ER-диаграмма БД")

Таблицы:

- `acquisition` — информация о покупках одних компаний другими
  - первичный ключ `id` — идентификатор или уникальный номер покупки
  - внешний ключ `acquiring_company_id` — ссылается на таблицу `company` — идентификатор компании-покупателя, то есть той, что покупает другую компанию
  - внешний ключ `acquired_company_id` — ссылается на таблицу `company` — идентификатор компании, которую покупают
  - `term_code` — способ оплаты сделки
    - `cash` — наличными
    - `stock` — акциями компании
    - `cash_and_stock` — смешанный тип оплаты: наличные и акции
  - `price_amount` — сумма покупки в долларах
  - `acquired_at` — дата совершения сделки
  - `created_at` — дата и время создания записи в таблице
  - `updated_at` — дата и время обновления записи в таблице

- `company` — информация о компаниях-стартапах
  - первичный ключ `id` — идентификатор, или уникальный номер компании
  - `name` — название компании
  - `category_code` — категория деятельности компании, например
    - `news` — специализируется на работе с новостями
    - `social` — специализируется на социальной работе
  - `status` — статус компании
    - `acquired` — приобретена
    - `operating` — действует
    - `ipo` — вышла на IPO
    - `closed` — перестала существовать
  - `founded_at` — дата основания компании
  - `closed_at` — дата закрытия компании, которую указывают в том случае, если компании больше не существует
  - `domain` — домен сайта компании
  - `twitter_username` — название профиля компании в твиттере
  - `country_code` — код страны, например, `USA` для США, `GBR` для Великобритании
  - `investment_rounds` — число раундов, в которых компания участвовала как инвестор
  - `funding_rounds` — число раундов, в которых компания привлекала инвестиции
  - `funding_total` — сумма привлечённых инвестиций в долларах
  - `milestones` — количество важных этапов в истории компании
  - `created_at` — дата и время создания записи в таблице
  - `updated_at` — дата и время обновления записи в таблице

- `education` — информация об уровне образования сотрудников компаний
  - первичный ключ `id` — уникальный номер записи с информацией об образовании
  - внешний ключ `person_id` — ссылается на таблицу `people` — идентификатор человека, информация о котором представлена в записи
  - `degree_type` — учебная степень, например
    - `BA` — Bachelor of Arts — бакалавр гуманитарных наук
    - `MS` — Master of Science — магистр естественных наук
  - `instituition` — учебное заведение, название университета
  - `graduated_at` — дата завершения обучения, выпуска
  - `created_at` — дата и время создания записи в таблице
  - `updated_at` — дата и время обновления записи в таблице

- `fund` — информация о венчурных фондах. 
  - первичный ключ `id` — уникальный номер венчурного фонда
  - `name` — название венчурного фонда
  - `founded_at` — дата основания фонда
  - `domain` — домен сайта фонда
  - `twitter_username` — профиль фонда в твиттере
  - `country_code` — код страны фонда
  - `investment_rounds` — число инвестиционных раундов, в которых фонд принимал участие
  - `invested_companies` — число компаний, в которые инвестировал фонд
  - `milestones` — количество важных этапов в истории фонда
  - `created_at` — дата и время создания записи в таблице
  - `updated_at` — дата и время обновления записи в таблице

- `funding_round` — информация о раундах инвестиций. 
  - первичный ключ `id` — уникальный номер инвестиционного раунда
  - внешний ключ `company_id` — ссылается на таблицу `company` — уникальный номер компании, участвовавшей в инвестиционном раунде
  - `funded_at` — дата проведения раунда
  - `funding_round_type` — тип инвестиционного раунда, например
    - `venture` — венчурный раунд
    - `angel` — ангельский раунд
    - `series_a` — раунд А
  - `raised_amount` — сумма инвестиций, которую привлекла компания в этом раунде в долларах
  - `pre_money_valuation` — предварительная, проведённая до инвестиций оценка стоимости компании в долларах
  - `participants` — количество участников инвестиционного раунда
  - `is_first_round` — является ли этот раунд первым для компании
  - `is_last_round` — является ли этот раунд последним для компании
  - `created_at` — дата и время создания записи в таблице
  - `updated_at` — дата и время обновления записи в таблице

- `investment` — информация об инвестициях венчурных фондов в компании-стартапы
  - первичный ключ `id` — уникальный номер инвестиции
  - внешний ключ `funding_round_id` — ссылается на таблицу `funding_round` — уникальный номер раунда инвестиции
  - внешний ключ `company_id` — ссылается на таблицу `company` — уникальный номер компании-стартапа, в которую инвестируют
  - внешний ключ `fund_id` — ссылается на таблицу `fund` — уникальный номер фонда, инвестирующего в компанию-стартап
  - `created_at` — дата и время создания записи в таблице
  - `updated_at` — дата и время обновления записи в таблице

- `people` — информация о сотрудниках компаний-стартапов
  - первичный ключ `id` — уникальный номер сотрудника
  - `first_name` — имя сотрудника
  - `last_name` — фамилия сотрудника
  - внешний ключ `company_id` — ссылается на таблицу `company` — уникальный номер компании-стартапа
  - `twitter_username` — профиль сотрудника в твиттере
  - `created_at` — дата и время создания записи в таблице
  - `updated_at` — дата и время обновления записи в таблице

## Задача 1

Посчитайте, сколько компаний закрылось.

**Решение**

```sql
SELECT COUNT(status)
FROM company
WHERE status = 'closed'
```

| count |
| --- |
| 2584 |

## Задача 2

Отобразите количество привлечённых средств для новостных компаний США. Используйте данные из таблицы `company`. Отсортируйте таблицу по убыванию значений в поле `funding_total` .

**Решение**

```sql
SELECT SUM(funding_total) AS total
FROM company
WHERE country_code = 'USA' AND category_code = 'news'
GROUP BY name
ORDER BY total DESC
```

| total |
| --- |
| 6.22553e+08 |
| 2.5e+08 |
| 1.605e+08 |
| 1.28e+08 |
| 1.265e+08 |
| 7e+07 |
| ... |

## Задача 3

Найдите общую сумму сделок по покупке одних компаний другими в долларах. Отберите сделки, которые осуществлялись только за наличные с 2011 по 2013 год включительно.

**Решение**

```sql
SELECT SUM(price_amount)
FROM acquisition
WHERE term_code = 'cash'
    AND EXTRACT(YEAR FROM CAST(acquired_at AS DATE)) IN (2011, 2012, 2013)
```

| sum |
| --- |
| 1.37762e+11 |

## Задача 4

Отобразите имя, фамилию и названия аккаунтов людей в твиттере, у которых названия аккаунтов начинаются на `'Silver'`.

**Решение**

```sql
SELECT first_name, last_name, twitter_username
FROM people
WHERE twitter_username LIKE 'Silver%'
```

| first_name | last_name | twitter_username |
| --- | --- | --- |
| Rebecca | Silver | SilverRebecca |
| Silver | Teede | SilverMatrixx |
| Mattias | Guilotte | Silverreven |

## Задача 5

Выведите на экран всю информацию о людях, у которых названия аккаунтов в твиттере содержат подстроку `'money'`, а фамилия начинается на `'K'`.

**Решение**

```sql
SELECT *
FROM people
WHERE twitter_username LIKE '%money%'
    AND last_name LIKE 'K%'
```

| id | first_name | last_name | company_id | twitter_username | created_at | updated_at |
| --- | --- | --- | --- | --- | --- | --- |
| 63081 | Gregory | Kim |  | gmoney75 | 2010-07-13 03:46:28 | 2011-12-12 22:01:34 |

## Задача 6

Для каждой страны отобразите общую сумму привлечённых инвестиций, которые получили компании, зарегистрированные в этой стране. Страну, в которой зарегистрирована компания, можно определить по коду страны. Отсортируйте данные по убыванию суммы.

**Решение**

```sql
SELECT
    country_code,
    SUM(funding_total)
FROM company
GROUP BY country_code
ORDER BY SUM(funding_total) DESC
```

| country_code | sum |
| --- | --- |
| USA | 3.10588e+11 |
| GBR | 1.77056e+10 |
|  | 1.08559e+10 |
| CHN | 1.06897e+10 |
| CAN | 9.86636e+09 |
| IND | 6.14141e+09 |
| DEU | 5.76577e+09 |
| ... | ... |

## Задача 7

Составьте таблицу, в которую войдёт дата проведения раунда, а также минимальное и максимальное значения суммы инвестиций, привлечённых в эту дату.

Оставьте в итоговой таблице только те записи, в которых минимальное значение суммы инвестиций не равно нулю и не равно максимальному значению.

**Решение**

```sql
SELECT
    funded_at,
    MIN(raised_amount) AS min_raised,
    MAX(raised_amount) AS max_raised
FROM funding_round
GROUP BY funded_at
HAVING MIN(raised_amount) != 0 AND MIN(raised_amount) != MAX(raised_amount)
```

| funded_at | min_raised | max_raised |
| --- | --- | --- |
| 2012-08-22 | 40000 | 7.5e+07 |
| 2010-07-25 | 3.27825e+06 | 9e+06 |
| 2002-03-01 | 2.84418e+06 | 8.95915e+06 |
| 2010-10-11 | 28000 | 2e+08 |
| 2007-01-18 | 5.5e+06 | 2.3e+07 |
| 2007-02-27 | 1.29e+06 | 3.6e+07 |
| ... | ... | ... |

## Задача 8

Создайте поле с категориями:

- Для фондов, которые инвестируют в 100 и более компаний, назначьте категорию `high_activity`.
- Для фондов, которые инвестируют в 20 и более компаний до 100, назначьте категорию `middle_activity`.
- Если количество инвестируемых компаний фонда не достигает 20, назначьте категорию `low_activity`.

Отобразите все поля таблицы `fund` и новое поле с категориями.

**Решение**

```sql
SELECT
    *,
    CASE
        WHEN invested_companies >= 100 THEN 'high_activity'
        WHEN invested_companies >= 20 AND invested_companies < 100 THEN 'middle_activity'
        WHEN invested_companies < 20 THEN 'low_activity'
    END
FROM fund
```

| id | name | founded_at | domain | twitter_username | country_code | investment_rounds | invested_companies | milestones | created_at | updated_at | case |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 13131 |  |  |  |  |  | 0 | 0 | 0 | 2013-08-19 18:46:55 | 2013-08-19 19:55:07 | low_activity |
| 1 | Greylock Partners | 1965-01-01 | greylock.com | greylockvc | USA | 307 | 196 | 0 | 2007-05-25 20:18:23 | 2012-12-27 00:42:24 | high_activity |
| 10 | Mission Ventures | 1996-01-01 | missionventures.com |  | USA | 58 | 33 | 0 | 2007-06-05 05:24:58 | 2013-10-10 22:06:31 | middle_activity |
| 100 | Kapor Enterprises, Inc. |  | kei.com |  | USA | 2 | 1 | 0 | 2007-07-12 09:42:21 | 2008-11-21 05:41:53 | low_activity |
| ... | ... | ... | ... | ... | ... | ... | ... | ... | ... | ... | ... |

## Задача 9

Для каждой из категорий, назначенных в предыдущем задании, посчитайте округлённое до ближайшего целого числа среднее количество инвестиционных раундов, в которых фонд принимал участие. Выведите на экран категории и среднее число инвестиционных раундов. Отсортируйте таблицу по возрастанию среднего.

**Исходный код**

```sql
SELECT *,
       CASE
           WHEN invested_companies>=100 THEN 'high_activity'
           WHEN invested_companies>=20 THEN 'middle_activity'
           ELSE 'low_activity'
       END AS activity
FROM fund
```

**Решение**

```sql
SELECT
    CASE
        WHEN invested_companies>=100 THEN 'high_activity'
        WHEN invested_companies>=20 THEN 'middle_activity'
        ELSE 'low_activity'
    END AS activity,
    ROUND(AVG(investment_rounds))
FROM fund
GROUP BY activity
ORDER BY round
```

| activity | round |
| --- | --- |
| low_activity | 2 |
| middle_activity | 51 |
| high_activity | 252 |

## Задача 10

Проанализируйте, в каких странах находятся фонды, которые чаще всего инвестируют в стартапы. 

Для каждой страны посчитайте минимальное, максимальное и среднее число компаний, в которые инвестировали фонды этой страны, основанные с 2010 по 2012 год включительно. Исключите страны с фондами, у которых минимальное число компаний, получивших инвестиции, равно нулю. Выгрузите десять самых активных стран-инвесторов.

Отсортируйте таблицу по среднему количеству компаний от большего к меньшему, а затем по коду страны в лексикографическом порядке.

**Решение**

```sql
SELECT
    country_code,
    MIN(invested_companies),
    MAX(invested_companies),
    AVG(invested_companies)
FROM fund
WHERE EXTRACT(YEAR FROM founded_at) IN (2010, 2011, 2012)
GROUP BY country_code
HAVING MIN(invested_companies) != 0
ORDER BY AVG(invested_companies) DESC, country_code
LIMIT 10
```

| country_code | min | max | avg |
| --- | --- | --- | --- |
| BGR | 25 | 35 | 30 |
| CHL | 29 | 29 | 29 |
| UKR | 8 | 10 | 9 |
| LTU | 5 | 5 | 5 |
| IRL | 4 | 5 | 4.5 |
| KEN | 3 | 3 | 3 |
| LBN | 3 | 3 | 3 |
| MUS | 3 | 3 | 3 |
| JPN | 1 | 6 | 2.83333 |
| HKG | 2 | 3 | 2.66667 |

## Задача 11

Отобразите имя и фамилию всех сотрудников стартапов. Добавьте поле с названием учебного заведения, которое окончил сотрудник, если эта информация известна.

**Решение**

```sql
SELECT
    p.first_name,
    p.last_name,
    e.instituition
FROM people AS p
LEFT JOIN education AS e ON e.person_id = p.id
```

| first_name | last_name | instituition |
| --- | --- | --- |
| John | Green | Washington University, St. Louis |
| John | Green | Boston University |
| David | Peters | Rice University |
| Dan | Birdwhistell | University of Cambridge |
| Gal | Cohen | Tel Aviv University |
| Chris | Treadaway | University of Texas |
| Chris | Treadaway | Louisiana State University |
| Sam | Lessin | Harvard University |
| ... | ... | ... |

## Задача 12

Для каждой компании найдите количество учебных заведений, которые окончили её сотрудники. Выведите название компании и число уникальных названий учебных заведений. Составьте топ-5 компаний по количеству университетов.

**Решение**

```sql
SELECT
    c.name,
    COUNT(DISTINCT e.instituition)
FROM company AS c
LEFT JOIN people AS p ON p.company_id = c.id
LEFT JOIN education AS e ON e.person_id = p.id
GROUP BY c.id
ORDER BY count DESC
LIMIT 5
```

| name | count |
| --- | --- |
| Google | 167 |
| Yahoo! | 115 |
| Microsoft | 111 |
| Knight Foundation | 74 |
| Comcast | 66 |

## Задача 13

Составьте список с уникальными названиями закрытых компаний, для которых первый раунд финансирования оказался последним.

**Решение**

```sql
SELECT
    DISTINCT c.name
FROM company AS c
LEFT JOIN funding_round AS fr ON fr.company_id = c.id
WHERE c.status = 'closed' AND fr.is_first_round = 1 AND fr.is_last_round = 1
```

| name |
| --- |
| 10BestThings |
| 11i Solutions |
| 169 ST. |
| 1bib |
| ... |

## Задача 14

Составьте список уникальных номеров сотрудников, которые работают в компаниях, отобранных в предыдущем задании.

**Решение**

```sql
SELECT DISTINCT id
FROM people
WHERE company_id IN (
    SELECT
        c.id
    FROM company AS c
    LEFT JOIN funding_round AS fr ON fr.company_id = c.id
    WHERE c.status = 'closed' AND fr.is_first_round = 1 AND fr.is_last_round = 1
)
```

| id |
| --- |
| 62 |
| 97 |
| ... |

## Задача 15

Составьте таблицу, куда войдут уникальные пары с номерами сотрудников из предыдущей задачи и учебным заведением, которое окончил сотрудник.

**Решение**

```sql
SELECT
    DISTINCT p.id,
    e.instituition
FROM people AS p
INNER JOIN education AS e ON e.person_id = p.id
WHERE p.company_id IN (
    SELECT
        c.id
    FROM company AS c
    LEFT JOIN funding_round AS fr ON fr.company_id = c.id
    WHERE c.status = 'closed' AND fr.is_first_round = 1 AND fr.is_last_round = 1
)
```

| id | instituition |
| --- | --- |
| 349 | AKI |
| 349 | ArtEZ Hogeschool voor de Kunsten |
| 349 | Rijks Akademie |
| 699 | Imperial College |
| 779 | Harvard University |
| 779 | Stanford University |
| ... | ... |

## Задача 16

Посчитайте количество учебных заведений для каждого сотрудника из предыдущего задания. При подсчёте учитывайте, что некоторые сотрудники могли окончить одно и то же заведение дважды.

**Решение**

```sql
SELECT
    DISTINCT p.id,
    COUNT(e.instituition)
FROM people AS p
INNER JOIN education AS e ON e.person_id = p.id
WHERE p.company_id IN (
    SELECT
        c.id
    FROM company AS c
    LEFT JOIN funding_round AS fr ON fr.company_id = c.id
    WHERE c.status = 'closed' AND fr.is_first_round = 1 AND fr.is_last_round = 1
)
GROUP BY p.id
```

| id | count |
| --- | --- |
| 349 | 3 |
| 699 | 1 |
| 779 | 2 |
| 968 | 1 |

## Задача 17

Дополните предыдущий запрос и выведите среднее число учебных заведений (всех, не только уникальных), которые окончили сотрудники разных компаний. Нужно вывести только одну запись, группировка здесь не понадобится.

**Решение**

```sql
SELECT
    AVG(ci.count)
FROM (SELECT
        p.id,
        COUNT(e.instituition)
    FROM people AS p
    INNER JOIN education AS e ON e.person_id = p.id
    WHERE p.company_id IN (
        SELECT
            c.id
        FROM company AS c
        LEFT JOIN funding_round AS fr ON fr.company_id = c.id
        WHERE c.status = 'closed' AND fr.is_first_round = 1 AND fr.is_last_round = 1
    )
    GROUP BY p.id) AS ci
```

| avg | 
| --- |
| 1.41509 |

## Задача 18

Напишите похожий запрос: выведите среднее число учебных заведений (всех, не только уникальных), которые окончили сотрудники Facebook*.

*(сервис, запрещённый на территории РФ)

**Решение**

```sql
SELECT
    AVG(ci.count)
FROM (SELECT
        p.id,
        COUNT(e.instituition)
    FROM people AS p
    INNER JOIN education AS e ON e.person_id = p.id
    WHERE p.company_id IN (
        SELECT
            c.id
        FROM company AS c
        LEFT JOIN funding_round AS fr ON fr.company_id = c.id
        WHERE C.name = 'Facebook'
    )
    GROUP BY p.id) AS ci
```

| avg | 
| --- |
| 1.51111 |

## Задача 19

Составьте таблицу из полей:

- `name_of_fund` — название фонда
- `name_of_company` — название компании
- `amount` — сумма инвестиций, которую привлекла компания в раунде.

В таблицу войдут данные о компаниях, в истории которых было больше шести важных этапов, а раунды финансирования проходили с 2012 по 2013 год включительно.

**Решение**

```sql
SELECT
    f.name AS name_of_fund,
    c.name AS name_of_company,
    fr.raised_amount AS amount
FROM investment AS i
LEFT JOIN company AS c ON c.id = i.company_id
LEFT JOIN fund AS f ON f.id = i.fund_id
INNER JOIN  (
    SELECT *
    FROM funding_round
    WHERE EXTRACT(YEAR FROM funded_at) IN (2012, 2013)
) AS fr ON fr.id = i.funding_round_id
WHERE c.milestones > 6
```

| name_of_fund | name_of_company | amount |
| --- | --- | --- |
| SAP Ventures | OpenX | 2.50112e+07 |
| Samsung Ventures | OpenX | 2.50112e+07 |
| Index Ventures | OpenX | 2.50112e+07 |
| Presidio Ventures | OpenX | 2.50112e+07 |
| DAG Ventures | Gigya | 2.5e+07 |
| DAG Ventures | Gigya | 1.53e+07 |
| Accel Partners | OpenX | 2.50112e+07 |
| Benchmark | Gigya | 2.5e+07 |
| Benchmark | Gigya | 1.53e+07 |
| Greenspring Associates | Gigya | 2.5e+07 |
| Mayfield Fund | Gigya | 2.5e+07 |
| Mayfield Fund | Gigya | 1.53e+07 |
| Mitsui Global Investment | OpenX | 2.50112e+07 |
| Advance Publication | Gigya | 1.53e+07 |

## Задача 20

Выгрузите таблицу, в которой будут такие поля:

- название компании-покупателя
- сумма сделки
- название компании, которую купили
- сумма инвестиций, вложенных в купленную компанию
- доля, которая отображает, во сколько раз сумма покупки превысила сумму вложенных в компанию инвестиций, округлённая до ближайшего целого числа.

Не учитывайте те сделки, в которых сумма покупки равна нулю. Если сумма инвестиций в компанию равна нулю, исключите такую компанию из таблицы. 

Отсортируйте таблицу по сумме сделки от большей к меньшей, а затем по названию купленной компании в лексикографическом порядке. Ограничьте таблицу первыми десятью записями.

**Решение**

```sql
WITH
acquiring AS (
    SELECT c.name AS buyer,
    a.price_amount AS price,
    a.id AS KEY
    FROM acquisition AS a
    LEFT JOIN company AS c ON a.acquiring_company_id = c.id
    WHERE a.price_amount > 0
),
acquired AS (
    SELECT c.name AS acquisition,
    c.funding_total AS investment,
    a.id AS KEY
    FROM acquisition AS a
    LEFT JOIN company AS c ON a.acquired_company_id = c.id
    WHERE c.funding_total > 0
)
SELECT
    acqn.buyer,
    acqn.price,
    acqd.acquisition,
    acqd.investment,
    ROUND(acqn.price / acqd.investment) AS uplift
FROM acquiring AS acqn
JOIN acquired AS acqd ON acqn.KEY = acqd.KEY
ORDER BY price DESC, acquisition
LIMIT 10
```

| buyer | price | acquisition | investment | uplift |
| --- | --- | --- | --- | --- |
| Microsoft | 8.5e+09 | Skype | 7.6805e+07 | 111 |
| Scout Labs | 4.9e+09 | Varian Semiconductor Equipment Associates | 4.8e+06 | 1021 |
| Broadcom | 3.7e+09 | Aeluros | 7.97e+06 | 464 |
| Broadcom | 3.7e+09 | NetLogic Microsystems | 1.88527e+08 | 20 |
| Level 3 Communications | 3e+09 | Global Crossing | 4.1e+07 | 73 |
| Yahoo! | 2.87e+09 | GeoCities | 4e+07 | 72 |
| eBay | 2.6e+09 | Skype | 7.6805e+07 | 34 |
| Salesforce | 2.5e+09 | ExactTarget | 2.3821e+08 | 10 |
| Johnson & Johnson | 2.3e+09 | Crucell | 4.43e+08 | 5 |
| IAC | 1.85e+09 | Ask.com | 2.5e+07 | 74 |

## Задача 21

Выгрузите таблицу, в которую войдут названия компаний из категории `social`, получившие финансирование с 2010 по 2013 год включительно. Проверьте, что сумма инвестиций не равна нулю. Выведите также номер месяца, в котором проходил раунд финансирования.

**Решение**

```sql
SELECT
    c.name,
    EXTRACT(MONTH FROM fr.funded_at)
FROM company AS c
JOIN funding_round AS fr ON fr.company_id = c.id
WHERE c.category_code = 'social'
    AND EXTRACT(YEAR FROM fr.funded_at) IN (2010, 2011, 2012, 2013)
    AND fr.raised_amount != 0
```

| name | date_part |
| --- | --- |
| Klout | 1 |
| WorkSimple | 3 |
| HengZhi | 1 |
| Twitter | 1 |
| SocialGO | 1 |
| ThisNext | 1 |
| Tagged | 1 |
| LikeMe.Net | 2 |
| Busuu | 10 |
| NetBase Solutions | 3 |
| ShopIgniter | 3 |
| Cascaad (CircleMe) | 2 |
| betaworks | 3 |
| ... | ... |

## Задача 22

Отберите данные по месяцам с 2010 по 2013 год, когда проходили инвестиционные раунды. Сгруппируйте данные по номеру месяца и получите таблицу, в которой будут поля:

- номер месяца, в котором проходили раунды
- количество уникальных названий фондов из США, которые инвестировали в этом месяце
- количество компаний, купленных за этот месяц
- общая сумма сделок по покупкам в этом месяце.

**Решение**

```sql
WITH
ufnc AS (
SELECT
    EXTRACT(MONTH FROM fr.funded_at) AS month,
    COUNT(DISTINCT f.name) AS unique_fund_name_count
FROM funding_round AS fr
JOIN investment AS i ON i.funding_round_id = fr.id
JOIN fund AS f ON f.id = i.fund_id
WHERE EXTRACT(YEAR FROM fr.funded_at) IN (2010, 2011, 2012, 2013)
    AND f.country_code = 'USA'
GROUP BY month
),
ac AS (
SELECT
    EXTRACT(MONTH FROM acquired_at) AS month,
    COUNT(acquired_company_id) AS acquired_company_count,
    SUM(price_amount) AS price_amount
FROM acquisition
WHERE EXTRACT(YEAR FROM acquired_at) IN (2010, 2011, 2012, 2013)
GROUP BY month
)

SELECT
    ac.month,
    ufnc.unique_fund_name_count,
    ac.acquired_company_count,
    ac.price_amount
FROM ufnc
JOIN ac ON ac.month = ufnc.month
```

| month | unique_fund_name_count | acquired_company_count | price_amount |
| --- | --- | --- | --- |
| 1 | 815 | 600 | 2.71083e+10 |
| 2 | 637 | 418 | 4.13903e+10 |
| 3 | 695 | 458 | 5.95016e+10 |
| 4 | 718 | 411 | 3.03837e+10 |
| 5 | 695 | 532 | 8.60122e+10 |
| 6 | 785 | 525 | 5.20883e+10 |
| 7 | 803 | 488 | 4.98541e+10 |
| 8 | 726 | 454 | 7.77093e+10 |
| 9 | 793 | 491 | 6.97409e+10 |
| 10 | 764 | 473 | 4.85567e+10 |
| 11 | 661 | 414 | 4.79386e+10 |
| 12 | 590 | 433 | 3.74251e+10 |

## Задача 23

Составьте сводную таблицу и выведите среднюю сумму инвестиций для стран, в которых есть стартапы, зарегистрированные в 2011, 2012 и 2013 годах. Данные за каждый год должны быть в отдельном поле. Отсортируйте таблицу по среднему значению инвестиций за 2011 год от большего к меньшему.

**Решение**

```sql
WITH
fc_2011 AS (
    SELECT
        country_code AS country,
        AVG(funding_total) AS funding_2011
    FROM company
    WHERE EXTRACT(YEAR FROM founded_at) = 2011
    GROUP BY country
),
fc_2012 AS (
    SELECT
        country_code AS country,
        AVG(funding_total) AS funding_2012
    FROM company
    WHERE EXTRACT(YEAR FROM founded_at) = 2012
    GROUP BY country
),
fc_2013 AS (
    SELECT
        country_code AS country,
        AVG(funding_total) AS funding_2013
    FROM company
    WHERE EXTRACT(YEAR FROM founded_at) = 2013
    GROUP BY country
)

SELECT
    fc_2011.country,
    fc_2011.funding_2011,
    fc_2012.funding_2012,
    fc_2013.funding_2013
FROM fc_2011
JOIN fc_2012 ON fc_2012.country = fc_2011.country
JOIN fc_2013 ON fc_2013.country = fc_2012.country
ORDER BY fc_2011.funding_2011 DESC
```

| country | funding_2011 | funding_2012 | funding_2013 |
| --- | --- | --- | --- |
| PER | 4e+06 | 41000 | 25000 |
| USA | 2.24396e+06 | 1.20671e+06 | 1.09336e+06 |
| HKG | 2.18078e+06 | 226227 | 0 |
| PHL | 1.75e+06 | 4218.75 | 2500 |
| ARE | 1.718e+06 | 197222 | 35333.3 |
| JPN | 1.66431e+06 | 674720 | 50000 |
| AUT | 1.5342e+06 | 147806 | 85773.3 |
| BRA | 1.38007e+06 | 240639 | 67944.4 |
| DEU | 1.1288e+06 | 1.32915e+06 | 66612.7 |
| ... | ... | ... | ... |