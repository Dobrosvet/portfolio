<!--
- ❗ сделать в исходных местах отшлифованные версии работ затем поместить сюда
- ❗ потом этот список работ поместить в README
- ❗ написать когда выполнены работы
- ❗ сделать на двух языках

Для генерации таблиц использовался
https://www.tablesgenerator.com/html_tables

Спринт 1. НЕТ ПРОЕКТА
Спринт 3. НЕТ ПРОЕКТА
Спринт 4. НЕТ ПРОЕКТА
Спринт 19. НЕТ ПРОЕКТА
Спринт 30. НЕТ ПРОЕКТА (тоже самое что и 29 спринт)

Данные по вакансиям
https://easyoffer.ru/
-->
# Data Science в Яндекс Практикум<span id="beginning"></span>

## Навигация по портфолио

Использовались: Python, Anaconda, VSCode

Базовое окружение которое использовалось для всех работ:
- [ds_practicum_env.yml](ds_practicum_env.yml)

### Топ интересных работ

1. [Поиск изображений соответствующих описанию](joint_image_text_based_retrieval/README.ru.md)
2. [Предсказание оттока клиентов отеля](hotel_customers_outflow_prediction/README.ru.md)
3. [Предсказание температуры звёзд](star_temperature_predict/README.ru.md)
4. [Оценка рисков ДТП](car_accident_risks/README.ru.md)
5. [Предсказание стоимости жилья с помощью SparkML](spark_prediction_house_cost/README.ru.md)
6. [Локация скважины](wells_location/README.ru.md)
7. [Базовый SQL](sql_basic/README.ru.md)
8. [Продвинутый SQL](sql_advanced/README.ru.md)
9. [Объявления о продаже квартир](apartment_sales_ads/README.ru.md)
10. [Российский кинопрокат](russian_film_distribution/README.ru.md)
<!--
11. [Надёжность заёмщиков](borrower_reliability/README.ru.md)
-->

### Все работы в хронологическом порядке

<table>
<thead>
  <tr>
    <th>#</th>
    <th>Название проекта</th>
    <th>Файлы</th>
    <th>Стек</th>
  </tr>
</thead>
<tbody>
  <!-- <tr id="">
    <td>1</td>
    <td><a href="">Исследование по роботам</a></td>
    <td>Описание</td>
    <td>Стек</td>
    '- Тут можно но не обязательно сформировать ipynb-блокнот по теме "Основы Python и анализа данных"<br>- `bots_research`
  </tr> -->
  <tr id="comparing_music_between_cities">
    <td>2</td>
    <td><a href="comparing_music_between_cities/README.ru.md">Яндекс Музыка в Москве и Санкт-Петербурге</a></td>
    <td>Сделано сравнение Москвы и Петербурга по музыкальным жанрам и проверены гипотезы</td>
    <td>pandas</td>
    <!--
    - `comparing_music_between_cities.ipynb`<br>- `comparing_music_between_cities.csv`
    -->
  </tr>
  <tr id="borrower_reliability">
    <td>3</td>
    <td><a href="borrower_reliability/README.ru.md">Надёжность заёмщиков</a></td>
    <td>Построена модель кредитного скоринга для оценки способности потенциального заёмщика вернуть кредит банку</td>
    <td>pandas, seaborn, math, предобработка данных</td>
    <!--⭐
    - `borrower_reliability.ipynb`<br>- `data.csv` ← переименовать в `borrower_reliability.csv`
    -->
  </tr>
  <tr id="apartment_sales_ads">
    <td>4</td>
    <td><a href="apartment_sales_ads/README.ru.md">Объявления о продаже квартир</a></td>
    <td>Сделан анализ и определены характеристики для установки рыночной стоимости объектов недвижимости</td>
    <td>pandas, seaborn, geopy, EDA</td>
    <!--⭐
    - `apartment_sales_ads.ipynb`<br>- `real_estate_data.csv` переименовать в `apartment_sales_ads.csv`
    -->
  </tr>
  <tr id="russian_film_distribution">
    <td>5</td>
    <td><a href="russian_film_distribution/README.ru.md">Российский кинопрокат</a></td>
    <td>Выявлены текущие тренды кинопроката</td>
    <td>numpy, pandas, EDA</td>
    <!--⭐
    - `russian_film_distribution.ipynb`<br>- `mkrf_movies.csv`<br>- `mkrf_shows.csv`
    -->
  </tr>
  <tr id="best_tariff">
    <td>6</td>
    <td><a href="best_tariff/README.ru.md">Лучший тариф</a></td>
    <td>Определён лучший тариф по данным мобильного оператора</td>
    <td>numpy, pandas, seaborn, EDA, проверка гипотез</td>
  </tr>
    <!--
    - `best_tariff.ipynb`<br>- `calls.csv`<br>- `internet.csv`<br>- `messages.csv`<br>- `tariffs.csv`<br>- `users.csv`
    -->
  <tr id="tariff_recommendation">
    <td>7</td>
    <td><a href="tariff_recommendation/README.ru.md">Рекомендация тарифов</a></td>
    <td>Создана модель для рекомендации тарифа клиенту</td>
    <td>sklearn, seaborn, pandas, классификация</td>
  </tr>
    <!--
    - `tariff_recommendation.ipynb`<br>- `users_behavior.csv`
    -->
  <tr id="bank_customers_outflow">
    <td>8</td>
    <td><a href="bank_customers_outflow/README.ru.md">Отток клиентов банка</a></td>
    <td>Создана модель для предсказания, откажется ли клиент от услуг банка</td>
    <td>sklearn, matplotlib, seaborn, pandas, классификация</td>
    <!--❓ может добавить к избранным
    - `bank_customers_outflow.ipynb`
    - `churn.csv`
    -->
  </tr>
  <tr id="wells_location">
    <td>9</td>
    <td><a href="wells_location/README.ru.md">Локация скважины</a></td>
    <td>Создана модель для выявления самой прибыльной скважины</td>
    <td>sklearn, matplotlib, seaborn, pandas, numpy, locale, регрессия, бутстреп</td>
    <!--⭐
    - `wells_location.ipynb`
    - `geo_data_0.csv`
    - `geo_data_1.csv`
    - `geo_data_2.csv`
    -->
  </tr>
  <tr id="hotel_customers_outflow_prediction">
    <td>10</td>
    <td><a href="hotel_customers_outflow_prediction/README.ru.md">Предсказание оттока клиентов отеля</a></td>
    <td>Создана модель для предсказания отказа от брони клиентом отеля</td>
    <td>sklearn, OrdinalEncoder, GridSearchCV, RandomForestClassifier, DecisionTreeClassifier</td>
    <!--
    Спринт 14⭐💯1️⃣
    - `hotel_customers_outflow_prediction.ipynb`
    - `hotel_train.csv`
    - `hotel_test.csv`
    -->
  </tr>
  <tr id="sql_basic">
    <td>11</td>
    <td><a href="sql_basic/README.ru.md">Базовый SQL</a></td>
    <td>Выполнен базовый набор SQL запросов</td>
    <td>SQL</td>
    <!--
    - `sql_basic.md`
    -->
  </tr>
  <tr id="git">
    <td>12</td>
    <td><b>Git - система контроля версий</b></td>
    <td>Этот репозиторий пример работы с Git и GitHub</td>
    <td>Git, GitHub</td>
    <!-- Можно показать владение в разных ситуациях через mermaid схемы Git для каких нибудь самых частых сценариев -->
  </tr>
  <!-- <tr id="">
    <td>13</td>
    <td><a href="">Предсказание плотности микробизнесов (мастерская)</a></td>
    <td>- `godaddy_microbusiness_density_forecasting.ipynb`<br>- `train.csv` ← Переименовать<br>- `test.csv` ← Переименовать<br>- `sample_submission.csv` ← Переименовать<br>- `census_starter.csv` ← Переименовать</td>
  </tr> -->
  <tr id="spark_prediction_house_cost">
    <td>14</td>
    <td><a href="spark_prediction_house_cost/README.ru.md">Предсказание стоимости жилья с помощью SparkML</a></td>
    <td>Создана модель для предсказания стоимости жилья и сравнение результатов с и без категориальных признаков</td>
    <td>pyspark, pandas, seaborn, spark, big data, регрессия</td>
    <!--⭐
    - `spark_prediction_house_cost.ipynb`<br>- Датасет удалённый
    -->
  </tr>
  <tr id="clients_personal_data_protection">
    <td>15</td>
    <td><a href="clients_personal_data_protection/README.ru.md">Защита персональных данных клиентов</a></td>
    <td>Разработан метод скрытия персональных данных клиентов, с помощью матричных операций, без снижения качества модели</td>
    <td>sklearn, pandas, numpy, seaborn, matplotlib, линейная алгебра, регрессия</td>
    <!--❓ может добавить к избранным
    - `clients_personal_data_protection.ipynb`<br>- `insurance.csv`
    -->
  </tr>
  <tr id="cars_cost_prediction">
    <td>16</td>
    <td><a href="cars_cost_prediction/README.ru.md">Определение стоимости автомобилей</a></td>
    <td>Разработана модель для определения стоимости автомобиля по характеристикам</td>
    <td>catboost, xgboost, lightgbm, sklearn, joblib, регрессия, градиентный бустинг</td>
    <!--
    - `cars_cost_prediction.ipynb`<br>- `autos.csv`
    -->
  </tr>
  <!-- <tr id="">
    <td>17</td>
    <td><a href="">Определение сложности английского в фильме (мастерская 2)</a></td>
    <td>- `english_movies_complexity_score.ipynb`<br>- `movies.csv`<br>- все сопутствующие материалы вроде фалов субтитров</td>
  </tr> -->
  <tr id="sql_advanced">
    <td>18</td>
    <td><a href="sql_advanced/README.ru.md">Продвинутый SQL</a></td>
    <td>Выполнен продвинутый набор SQL запросов</td>
    <td>SQL</td>
    <!--
    - `sql_advanced.ipynb`<br>- подключение к БД в переменные окружения что бы их не было в репозитории
    -->
  </tr>
  <!-- <tr id="">
    <td>19</td>
    <td><a href="">Практика SQL (дополнительный спринт)</a></td>
    <td></td>
  </tr> -->
  <tr id="star_temperature_predict">
    <td>20</td>
    <td><a href="star_temperature_predict/README.ru.md">Предсказание температуры звёзд</a></td>
    <td>Создана собственная полносвязная нейросеть для определения температуры звезды</td>
    <td>torch, Sequential, Adamax, Linear, ReLU, Dropout, BatchNorm1d, ml алгоритмы</td>
    <!--⭐💯2️⃣
    - `star_temperature_predict.ipynb`<br>- `6_class.csv` ← переименовать в `star_temperature.csv`
    -->
  </tr>
  <tr id="car_accident_risks">
    <td>21</td>
    <td><a href="car_accident_risks/README.ru.md">Оценка рисков ДТП</a></td>
    <td>Для каршеринга сделан анализ факторов риска ДТП и модель для предупреждения водителя об уровне опасности на выбранном маршруте</td>
    <td>catboost, lightgbm, sklearn, SQL, sklearn, sqlalchemy, plotly</td>
    <!--⭐
    - `car_accident_risks.ipynb`<br>- вынести внешнее подключение в переменных окружения `.env`
    -->
  </tr>
  <tr id="taxi_orders_prediction">
    <td>22</td>
    <td><a href="taxi_orders_prediction/README.ru.md">Предсказание заказов такси</a></td>
    <td>Создана модель для предсказания заказов такси на следующий час</td>
    <td>xgboost, sklearn, statsmodels, временные ряды, регрессия</td>
    <!--⭐
    - `taxi_orders_prediction.ipynb`
    - `taxi.csv`
    -->
  </tr>
  <tr id="toxic_comments_detection">
    <td>23</td>
    <td><a href="toxic_comments_detection/README.ru.md">Определение токсичных комментариев с BERT</a></td>
    <td>Создана модель для определения степени токсичности комментария</td>
    <td>transformers, torch, sklearn, pandas, tqdm, BERT, NLP</td>
    <!--
    - `toxic_comments_detection.ipynb`
    - `toxic_comments.csv`
    -->
  </tr>
  <tr id="age_prediction_cv">
    <td>24</td>
    <td><a href="age_prediction_cv/README.ru.md">Определение возраста покупателей</a></td>
    <td>Создана модель для определения возраста покупателя по изображению</td>
    <td>keras, pandas, matplotlib, ResNet, imagenet, CV</td>
    <!--
    - `age_prediction_cv.ipynb`
    - Данные взяты с сайта [ChaLearn Looking at People](http://chalearnlap.cvc.uab.es/dataset/26/description/)
    - `labels.csv`
    - папка с изображениями
    -->
  </tr>
  <tr id="joint_image_text_based_retrieval">
    <td>25</td>
    <td><a href="joint_image_text_based_retrieval/README.ru.md">Поиск изображений соответствующих описанию</a></td>
    <td>Создана модель для определения сходства изображения и текста</td>
    <td>keras_nlp, keras, ResNet50, tensorflow, nltk, sklearn, pillow, BERT, NLP, CV, эмбеддинги</td>
    <!--⭐💯3️⃣
    - `joint_image_text_based_retrieval.ipynb`<br>- Папка `data`
    -->
  </tr>
  <tr id="steel_temperature_prediction">
    <td>26</td>
    <td><a href="steel_temperature_prediction/README.ru.md">Предсказание температуры стали в промышленности</a></td>
    <td>Сделана модель для предсказания температуры стали и имитации технологического процесса</td>
    <td>keras, tensorflow, catboost, optuna, sklearn, sqlalchemy, dotenv</td>
    <!--
    - `steel_temperature_prediction.ipynb`
    - вынести внешнее подключение в переменных окружения `.env`
    -->
  </tr>
  <!-- <tr id="">
    <td>27</td>
    <td><a href="">Диагностика базовой математики (дополнительный спринт)</a></td>
    <td></td>
  </tr> -->
</tbody>
</table>