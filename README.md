![logo](./images/cityline-vector-logo.jpg)

# <center> Финальный проект: Модель прогнозирования стоимости жилья для агентства недвижимости  </center>

## Оглавление
1. [Описание проекта](#Описание-проекта)
2. [Описание данных](#Описание-данных)
3. [Зависимости](#Зависимости)
4. [Установка проекта](#Установка-проекта)
5. [Использование проекта](#Использование-проекта)
6. [Выводы](Использование-проекта)

## Описание проекта

**Данный проект** - это дипломная работа по итогам курса *Data Science*.

Агентство недвижимости столкнулось с проблемой — риелторы тратят слишком много времени на сортировку объявлений и поиск выгодных предложений. Поэтому скорость их реакции и качество анализа не дотягивают до уровня конкурентов. Это сказывается на финансовых показателях агентства.

Наша цель — разработать модель машинного обучения, которая поможет обрабатывать объявления и увеличит число сделок и прибыль агентства.

**О структуре проекта:**
* [images](./images) - папка с изображениями, необходимыми для проекта.
* [data](./data) - папка с данными (таблицы с географическими данными полученные парсингом геосайтов, а также таблицы из википедии).
* [Project_Final.ipynb](./Project_Final.ipynb) - jupyter-ноутбук, содержащий основной код проекта: чтение и обработка датасета, подготовка данных к моделированию, обучение нескольких различных моделей.
* [parser_city_info.ipynb](./parser_city_info.ipynb) - парсер для нахождения данных по городам.
* [parser_coordinates.ipynb](./parser_coordinates.ipynb) - парсер для нахождения географических координат по адресу.
* [Brief.pdf](./Brief.pdf) - бриф проекта.


## Описание данных

Исходные данные представляют собой таблицу с около 380К наблюдений (объектов недвижимости) со следующими признаками:
- *status* — статус продажи;
- *private pool* и *PrivatePool* — наличие собственного бассейна;
- *propertyType* — тип объекта недвижимости;
- *street* — адрес объекта;
- *baths* — количество ванных комнат;
- *homeFacts*' — сведения о строительстве объекта, содержит несколько типов сведений, влияющих на оценку объекта:
    * *Year built* — год постройки;
    * *Remodeled year* — год реновации;
    * *Heating* — отопление;
    * *Cooling* — кондиционирование;
    * *Parking* — парковка;
    * *lotsize* — размер участка;
    * *Price/sqft* — цена за квадратный фут;
- *fireplace* — наличие камина;
- *city* — город;
- *schools* — сведения о школах в районе, содержат сведения:
    * *rating* — рейтинги школ поблизости;
    * *Distance* — расстояние до этих школ;
    * *Grades* — тип школы (начальная, средняя, частная и пр.);
    * *name* — название школы;
- *sqft* — площадь в квадратных футах;
- *zipcode* — почтовый индекс;
- *beds* — количество спален;
- *state* — штат;
- *stories* — количество этажей;
- *mls-id* и *MlsId* — идентификатор *MLS* (*Multiple Listing Service*, система мультилистинга);
- ***target*** — цена объекта недвижимости (целевой признак, который необходимо спрогнозировать).

Более подробно можно посмореть в [брифе](./Brief.pdf)

Данные имеют большое количество пропусков и требуют предварительной подготовки.

**Примечание**. В коде присутствует парсинг (совсем немного), но код может работать и без него.

## Используемые зависимости
* Python (3.9):
    * [pandas (1.3.4)](https://pandas.pydata.org)
    * [numpy (1.23.5)](https://pypi.org/project/psycopg2/)
    * [seaborn (0.13.0)](https://plotly.com/python/)
    * [matplotlib (3.6.3)](https://matplotlib.org/)
    * [scikit-learn (1.2.2)](https://scikit-learn.org/stable/index.html)
    * [category-encoders (2.6.1)](https://contrib.scikit-learn.org/category_encoders/)
    * [catboost (1.2)](https://catboost.ai/)
    * [beautifulsoup4==4.12.0](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)
    * [scipy==1.9.3](https://docs.scipy.org/doc/scipy-1.9.3/tutorial/index.html)
    * [wikipedia==1.4.0](https://wikipedia.readthedocs.io/en/latest/quickstart.html#quickstart)
    * [urllib3==2.0.3](https://urllib3.readthedocs.io/en/stable/)
 
## Установка проекта
```
git clone https://github.com/MaximZhambalov/Project_Final
```
Датасет по проекту можно найти [здесь.](https://disk.yandex.ru/d/NRDajlYMtq8f4w)

## Использование
Загрузка, предобработка и обучение модели находятся в *jupyter*-ноутбуке **Project_Final.ipynb**. В ноутбуках **parser_city_info.ipynb** и **parser_coordinates.ipynb** элементы парсинга географической информации.

## Выводы
В этом проекте:
- проведён разведовательный анализ данных, обработан и подготовлен датасет для модели;
- была построена модель, предсказывающая цену на недвижимость. Финальное значение метрик на тестовой *MAE = 80681*, *MAPE = 21.9%* и $R^2\ =\ 0.825$.