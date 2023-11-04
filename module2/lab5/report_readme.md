# *Лабораторная работа 2. Метод k-ближайших соседей (k-NN)*

## Введение
*[Отчет по лабораторной работе № 5](https://github.com/ITSamantha/artificial_intelligence_systems/edit/main/module2/lab5/readme.md)*
### Цель
Целью данной лабораторной работы является реализация метода k-ближайших соседей (k-NN) и его применение к набору данных о вине. Мы проведем предварительную обработку данных, реализуем метод k-NN без использования сторонних библиотек, кроме NumPy и Pandas, и оценим его производительность на тестовом наборе данных.
### Задача
- Студенты с четным порядковым номером в группе должны использовать набор данных о [вине] (https://www.kaggle.com/datasets/davorbudimir/winedataset).
- Проведите предварительную обработку данных, включая обработку отсутствующих значений, кодирование категориальных признаков и масштабирование.
- Реализуйте метод k-ближайших соседей без использования сторонних библиотек, кроме NumPy и Pandas.
- Постройте две модели k-NN с различными наборами признаков:
    - Модель 1: Признаки случайно отбираются.
    - Модель 2: Фиксированный набор признаков, который выбирается заранее.
- Для каждой модели проведите оценку на тестовом наборе данных при разных значениях k. Выберите несколько различных значений k, например, k=3, k=5, k=10, и т. д. Постройте матрицу ошибок.
  
## Описание метода
Метод k-ближайших соседей (k-NN) - это простой и популярный метод машинного обучения, который используется для классификации и регрессии. Его назначение заключается в том, чтобы определить метку (классификация) или значение (регрессия) нового объекта на основе меток и значений его ближайших соседей из обучающего набора данных.
Принцип работы метода k-NN следующий:
1. Загрузка обучающего набора данных, который содержит объекты с известными метками (для классификации) или значениями (для регрессии).
2. Предобработка данных, включая удаление отсутствующих значений, нормализацию (чтобы признаки имели одинаковый масштаб) и, при необходимости, кодирование категориальных признаков.
3. Загрузка тестового набора данных, для которого требуется определить метки (классификация) или значения (регрессия).
4. Для каждого объекта из тестового набора:
    - Расчет расстояния между этим объектом и каждым объектом из обучающего набора. Евклидово расстояние часто используется для этой цели, но можно использовать и другие метрики расстояния.
    - Отсортировать объекты обучающего набора по расстоянию в порядке возрастания.
    - Выбрать k ближайших соседей, где k - это гиперпараметр, который задается заранее.
    - Для классификации: определить класс объекта на основе меток k ближайших соседей. Например, можно выбрать класс, который является наиболее часто встречающимся среди соседей (большинство голосов).
5. Оценить производительность метода на тестовом наборе данных, используя метрики, такие как матрица ошибок, коэффициент F1, среднеквадратичная ошибка (для регрессии) и другие.
Метод k-NN прост в реализации и понимании, но может быть вычислительно затратным при больших объемах данных, так как требует вычисления расстояний между объектами. Выбор оптимального значения k является важной задачей при применении метода k-NN, так как недостаточно малое k может привести к переобучению, а слишком большое k может сделать метод менее чувствительным к локальным паттернам данных.

## Псевдокод метода
```
Функция euclidean_distance(x1, x2):
    Вычислить Евклидово расстояние между x1 и x2.
    Вернуть результат.

Функция predict(X):
    Преобразовать X в массив numpy.
    Создать пустой список y_pred для хранения предсказанных меток.
    Для каждого x в X:
        Создать пустой список distances для хранения расстояний.
        Для каждого x_train в обучающем_наборе:
            Вычислить расстояние между x и x_train с использованием euclidean_distance.
            Добавить расстояние в список distances.
        Найти индексы k ближайших соседей путем сортировки distances.
        Создать пустой список k_nearest_labels для хранения меток k ближайших соседей.
        Для каждого i в k_indices:
            Получить метку label из y_train соответствующую индексу i.
            Добавить метку label в k_nearest_labels.
        Найти наиболее часто встречающийся класс среди меток k ближайших соседей.
        Добавить этот класс в предсказанные значения.
    Вернуть массив предсказанных значений.
```

Этот псевдокод описывает основной алгоритм метода k-NN. Он подразумевает, что у вас есть обучающий набор данных с известными метками (для классификации) или значениями (для регрессии) и тестовый набор данных, для которого требуется предсказать метки или значения. Выбор значения k - это гиперпараметр.

## Результаты выполнения 
### Анализ данных и визуализация
Проанализирован набор данных и вычислена статистика, включая количество, среднее значение, стандартное отклонение, минимум, максимум и различные квантили для каждого признака. Визуализированы данные, чтобы лучше понять их распределение и корреляцию между признаками. Примеры визуализации данных были представлены в отчете.

- Описание датасета:

  ![image](https://github.com/ITSamantha/Artificial_Intelligence_Systems/assets/100091168/70d00899-42ca-43f2-b11f-3d444cb5cd13)
  ![image](https://github.com/ITSamantha/Artificial_Intelligence_Systems/assets/100091168/ee8efc0c-190b-4f6a-be85-7e622ca4ed04)

- Описание статистики атрибута:
  
  ![image](https://github.com/ITSamantha/Artificial_Intelligence_Systems/assets/100091168/90cea7cd-9714-4258-83ca-4d339a0d4d2a)

- Визуализация данных
  ![image](https://github.com/ITSamantha/Artificial_Intelligence_Systems/assets/100091168/2dca0a9a-735b-447c-9553-ce16a8f87e96)


### Предварительная обработка данных
В начале работы проведена предварительная обработка данных, включая обработку отсутствующих значений. Категориальные признаки не требовали кодирования, исходные данные были нормированы.

- Предварительная обработка данных

  ![image](https://github.com/ITSamantha/Artificial_Intelligence_Systems/assets/100091168/2e2693de-71f0-41db-9231-83dfca3dea7a)
  ![image](https://github.com/ITSamantha/Artificial_Intelligence_Systems/assets/100091168/9a9eb49e-1be6-404f-a523-5497cc60da85)

### Реализация метода k-ближайших соседей
Получение статистики реализовано с помощью библиотеки Pandas. Визуализация данных реализована с помощью библиотек Seaborn и matplotlib.pyplot. Кодирование категориальных признаков в данном случае не нужно, нормировка реализована.
Были построены модели с различными параметрами (параметры на каждом шаге выбираются рандомно, что позволяет оценить больший спектр моделей). Реализованы методы нахождения confusion matrix, f1_score.

### Построение модели
Мы построили две модели k-NN с различными наборами признаков:
- Модель 1: Признаки случайно отбирались.
- Модель 2: Использовался фиксированный набор признаков.

*Модели:*
  ![image](https://github.com/ITSamantha/Artificial_Intelligence_Systems/assets/100091168/25b56584-23b3-4461-a66b-079994fe6634)
  ![image](https://github.com/ITSamantha/Artificial_Intelligence_Systems/assets/100091168/a573dd4f-e62d-4d13-8451-3419ead5b751)
  ![image](https://github.com/ITSamantha/Artificial_Intelligence_Systems/assets/100091168/5cceb36b-a729-486a-b08f-f0cc882141a8)

### Оценка на тестовом наборе данных:
- Мы провели оценку производительности каждой модели на тестовом наборе данных при различных значениях k, включая k=3, k=5, k=10 и др.
- Для оценки использовались метрики, такие как коэффициент F1 (F1-score) и confusion matrix.

### Лучший показатель F1-score
Наилучший показатель коэффициента F1-score составил 1,0, что говорит о высокой эффективности модели.
Наиболее удачной оказалась модель с исходным набором атрибутов (13 атрибутов). 

## Примеры использования метода
Метод k-ближайших соседей может быть полезен во многих ситуациях, например:
1. Классификация электронных писем как спам или не спам на основе текстовых признаков.
2. Определение категории товаров на основе их описания и характеристик.
3. Рекомендация фильмов или продуктов на основе предпочтений пользователя и их схожести с другими пользователями.
4. Определение болезни пациента на основе его медицинских характеристик и анализа медицинских историй других пациентов.
Метод k-NN хорошо работает в задачах, где схожие объекты имеют схожие метки, и когда нет четкой структуры данных. Однако, он может быть вычислительно затратным при больших объемах данных, и выбор оптимального значения k играет важную роль в его производительности.