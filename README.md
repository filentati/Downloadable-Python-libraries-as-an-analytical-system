# Скачиваемы бмблиотеки Python как средство для анализа данных

Данный проект посвещен обзору на сказиваемые библеотеки Python для анализа и визуализации данный на примерах готовых датасетов: 

1. [Pandas](https://habr.com/ru/companies/ruvds/articles/494720/)
2. [Matplotlib.pyplot](https://habr.com/ru/articles/468295/)
3. [SeaBorn](https://habr.com/ru/companies/otus/articles/540526/)
4. [Plotly](https://habr.com/ru/articles/502958/) 

По ссылкам представленным выше можно ознакомится с возможностями с каждой из библеотек более подробно 

## Содержание 

- [Анализ готового датасет магазина](#Анализ готового датасет магазина)
    - [Подготовка к анализу данных](#Подготовка к анализу данных)
    - [Анализ и визуализация](#Анализ и визуализация)
- [Еще примеры по визуализации данных](#Ещё примеры по визаулизации данных)
- [RFM-сегментация](#RFM-сегментация)
- [Плюсы использования скачиваемых библеотек Python как аналитической системы](#Плюсы использования скачиваемых библеотек Python как аналитической системы)
- [Недостатки](#Недостатки)
- [Заключение](#Заключение)
	
## Анализ готового датасет магазина

Для анализа и визуализации данных будем использовать готовый датасет некоторого магазина с фиктивными данным. Датасет был скачен [Online retail dataset](https://datasetsearch.research.google.com/search?src=0&query=online%20retail&docid=L2cvMTF0c2g3YzlscA%3D%3D).

[Код анализа и визуализации данных этого датасета](https://github.com/filentati/Downloadable-Python-libraries-as-an-analytical-system/blob/main/data_analysis_store.ipynb)

### Подготовка к анализу данных

Для начала работа мы удаляем строки, которые содержат нулевые значения. Для этого мы используем методы из pandas. 
Следуещим шагом анализируем выбросы. Для визуализация текущей ситуации используем методы из matplotlib.pyplot для создания фигуры (окна) с двумя подграфиками и из seaborn для построения диагммы размаха [('ящика с усами')](https://habr.com/ru/articles/267123/).


### Анализ и визуализация

Спомощью методов библиотеки pandas была получина более подробная информацию о нашем датасети: какие есть клонки, какого типа данный содержатся в этих колонкках, сколько памяти испольуется. 
Так же для столбцов с числовыми данным с помощью методов pandas были расчитаны количества уникальных элемментнов в каждом из столбцов. А так же выведены статистические данные, такие как: среднее значение, минамальное и максимальное значения, межквартильных размах, стандартное отклонение. 

С помощью методов библиотеки Matplotlib.pyplot была построенна круговая диаграмма, показывающая в процентах количество покупок по странам. 

Но это далко не все возможности этих библеотек. Также Matplotlib.pyplot позволяет строить тепловые диаграммы, гистограмы с указанием функции плотности распределения и многое другое.

## Ещё примеры по визаулизации данных

Для постоенния визуализаций, представленных ниже, был использован [датасет с данными людьми, которые обращались в клинику по лечению рака](https://github.com/filentati/Downloadable-Python-libraries-as-an-analytical-system/blob/main/heart.csv). Датасет изначально был без выбрасов и пропущенных строк, поэтому дополнительных анализ не проводился.

[Код постоенния визуализаций](https://github.com/filentati/Downloadable-Python-libraries-as-an-analytical-system/blob/main/data_analysis_heart.ipynb)

Были постоенные с помощью Matplotlib.pyplot и SeaBorn
1) Диаграмма плотности распределения (Kernel Density Estimation plot, KDE plot) или иногда её называют диаграммой ядерной оценки плотности.
2) Гистаграму с функцией плотности распределения
3) И совмещенные тепловую диаграмму и гистограмму

Так же с помощью библиотеки plotly была потсоенна диаграмма рассеяния. Одно из преимуществ диграмма, полученных спомощью библеотеки plotly, - они являются интерактивными

## RFM-сегментация 

Так же скачиваемая библеотка pandas позволяет написать код для [RFM-сегментации](https://habr.com/ru/companies/mindbox/articles/420915/). Такая сегминтации позволяет разделить клиентов на сигменты по таким критериям как: R(Recency) — насколько давно клиент сделал последний заказ. F (Frequency) — сколько всего заказов сделал клиент. M(Monetary) — сколько денег клиент потрати. 
Это позволяет проанализировать ситуацию. Для увеличения продаж выбрают "лучшие" клиенты (клиенты, которые часто делают покупки и которые тратят больше денег в нашем магазине) для совершения рассылки с вознаграждением. Например: предложение скидки.
А так же выбрать клиентов, которые давно не совершали покупки, но потратили много денег, чтоб с помощью рассылки напомнить о нашем магазине. 

С помощью метода groupby из модуля Pandas был поятоенн датасет с параметрами Recency, Frequency, Monetary. 
Далее спомощью метода qcut из модуля Pandas мы делим на 4 группы клиентов по каждому из параметов Frequency, Monetary. Таким образом мы получаем 16 сегментов. По хорошему необходимо еще делать по параметку Recency, но в нашем датасети у всех клиентов дата последней покупки совпадает, поэтому они все попадают в один сегмент. 

После разделения на сегменты была построена круговая диаграмма количества клиентов в каждом из сегментов по параметру Monetary с помощью методов библиотеки Matplotlib.pyplot. По диаграмме можно заметить, что большинство клиентов находятся в 1 сегменте, то есть потратили небольшое количество денежных единиц в данном магазине. 

## Плюсы использования скачиваемых библеотек Python как аналитической системы

1. Расширяемость: все библиотке, которые были представленны имеют открытый исходный код, что позволяет изучить их работу, модифицировать их и создавать собственные расширения.
2. Гибкость: библиотеки легко интегрируются друг с другом, что позволяет создавать комплексные аналитические конвейеры.
3. При достаточном знание машинного обучения, с помощью скачиваемый библиотек (которые не были приведены), можно расширить и оптимизировать аназ и визуализацию данных 
4. Экономическая эффективность: бесплатное использование

## Недостатки 

1. Необходимо обладать доболнительными заниями: математической статистики, библиотек питона, отладки кодов
2. Управление зависимостями: конфликты версий, управление виртуальными окружениями, зависимости от внешних ресурсов

## Заключение 
В целом, преимущества использования скачиваемых библиотек Python для аналитических задач значительно перевешивают недостатки, особенно для проектов, требующих высокой эффективности, гибкости и расширяемости.
