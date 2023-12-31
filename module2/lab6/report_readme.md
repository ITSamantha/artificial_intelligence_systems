# *Лабораторная работа 3. Деревья решений*

## Введение
*[Отчет по лабораторной работе № 6](https://github.com/ITSamantha/artificial_intelligence_systems/blob/main/module2/lab6/readme.md)*

Деревья решений - это мощный метод машинного обучения, который широко используется для решения задач классификации и регрессии. Они представляют собой структуру данных, похожую на дерево, где каждый узел представляет собой условие, а каждое ребро ведет к другому узлу или листу дерева. В листьях дерева содержатся конечные классы или значения, которые позволяют проводить классификацию или регрессию для новых данных.
### Цель
В данной лабораторной работе была поставлена задача по реализации деревьев решений "с нуля" без использования сторонних библиотек, кроме NumPy и Pandas. Для этого был использован датасет с классификацией грибов на съедобные и несъедобные. Основной целью работы было построение дерева решений, оценка его производительности с использованием метрик Accuracy, Precision и Recall, а также построение кривых AUC-ROC и AUC-PR.
### Задача
1. Датасет с [классификацией грибов](https://archive.ics.uci.edu/ml/datasets/Mushroom).
2. Отобрать **случайным** образом sqrt(n) признаков
3. Реализовать без использования сторонних библиотек построение дерева решений (numpy и pandas использовать можно, использовать списки для реализации  дерева - нельзя)
4. Провести оценку реализованного алгоритма с использованием Accuracy, precision и recall
5. Построить AUC-ROC и AUC-PR (в пунктах 4 и 5 использовать библиотеки нельзя)
### Исходные данные
В качестве исходных данных был предоставлен датасет с информацией о различных видов грибов и их классификации на съедобные и несъедобные. Датасет включает в себя различные признаки (характеристики грибов) и целевую переменную, которая указывает на классификацию грибов.

## Описание метода
Метод деревьев решений - это алгоритм машинного обучения, который применяется для задач классификации и регрессии. Его назначение заключается в том, чтобы создать модель, которая на основе входных данных принимает решения и делает прогнозы.
Принцип работы деревьев решений можно описать следующим образом:
1. Начинается с корневого узла дерева, который представляет собой весь набор данных.
2. На каждом этапе выбирается признак, который лучше всего разделяет данные на две или более подгруппы. Выбор признака происходит так, чтобы максимизировать различие между классами или минимизировать ошибку в регрессии.
3. Данные разделяются на две подгруппы в соответствии с выбранным признаком, и для каждой подгруппы создается новый узел дерева.
4. Процесс разделения данных и создания новых узлов повторяется рекурсивно до выполнения критериев останова. Эти критерии могут включать в себя максимальную глубину дерева, минимальное количество объектов в листе, достижение чистоты классов и другие.
5. В листах дерева находятся конечные классы или значения, которые используются для классификации (в случае задачи классификации) или регрессии (в случае задачи регрессии).
6. После построения дерева, для новых данных происходит проход по дереву, начиная с корневого узла, и на каждом узле принимается решение о переходе к левому или правому поддереву в зависимости от значения соответствующего признака. Процесс продолжается до достижения листа, где получается прогноз.
Деревья решений могут быть использованы для разных типов задач:
- В задачах классификации, дерево решений позволяет определить класс объекта на основе его характеристик.
- В задачах регрессии, дерево решений предсказывает числовое значение на основе входных данных.
Однако деревья решений могут склонны к переобучению, поэтому важно правильно настраивать параметры модели, такие как максимальная глубина дерева, минимальное количество объектов в листе и другие. Также можно использовать ансамблевые методы, такие как случайный лес, для улучшения производительности и уменьшения переобучения.

## Псевдокод метода
```
Функция build_decision_tree(data, features):
    Если выполнились критерии останова (например, достигли максимальной глубины дерева или минимального количества объектов в листе):
        Создаем лист дерева и возвращаем его, присваивая ему прогноз для данной ветви.
    Иначе:
        Выбираем признак, который лучше всего разделяет данные на две подгруппы. Для этого исследуем все признаки и их значения.
        Разделяем данные на две подгруппы в соответствии с выбранным признаком и его значениями.
        Создаем два поддерева (левое и правое) и для каждого из них рекурсивно вызываем функцию build_decision_tree, передавая соответствующие подгруппы данных и признаки.
        Создаем узел дерева с выбранным признаком и ссылками на левое и правое поддерево.
        Возвращаем созданный узел дерева.
```

```
Функция classify(input_tree, feat_labels, test_vec):
    Получить метку признака для текущей вершины дерева (first_str)
    Получить словарь разветвлений для данной метки признака (second_dict)
    Найти индекс признака в списке feat_labels (feat_index)
    Получить значение тестируемого признака из входных данных (key)
    
    Получить результат классификации для данного значения признака (value_of_feat) из second_dict
    
    Если value_of_feat - это словарь:
        Рекурсивно вызвать функцию classify для этого словаря
        class_label будет равен результату классификации из рекурсивного вызова
    Иначе:
        class_label будет равен value_of_feat, что является конечной меткой класса
    
    Вернуть class_label как результат классификации для данного экземпляра данных
```

## Результаты выполнения 

### Выполненные шаги
1. Отбор случайных признаков. Сначала был выполнен случайный отбор признаков из исходного датасета. Для этого была использована техника "sqrt(n)" признаков, где "n" - это общее количество признаков в датасете.
2. Построение дерева решений: Был реализован алгоритм построения дерева решений без использования сторонних библиотек, за исключением библиотеки numpy и pandas.
3. Оценка производительности: Для оценки производительности построенного дерева решений были использованы следующие метрики:
    - Accuracy: Оценивает общую точность классификации.
    - Precision: Измеряет долю правильно классифицированных съедобных грибов относительно всех съедобных грибов.
    - Recall: Измеряет долю правильно классифицированных съедобных грибов относительно всех истинных съедобных грибов.
4. Построение кривых AUC-ROC и AUC-PR: Были построены кривые AUC-ROC и AUC-PR для оценки качества классификации. Кривая AUC-ROC оценивает, насколько хорошо модель разделяет съедобные и несъедобные грибы, а кривая AUC-PR оценивает точность и полноту классификации.

### Анализ данных и визуализация

- Описание датасета:

  ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/387ebd1c-3bf8-49cb-8a5f-8d661552fb9b)
  ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/1b18a82c-2e43-4ba7-91fd-8648bde939ff)
  ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/761f2fd8-73fc-4b86-aa25-8848553f7f4c)


- Описание статистики атрибутов:

  ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/54fe0707-d7c1-4e25-bc7b-f2d244ac5c5a)
  ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/ccd727c7-6e77-45bb-91c0-69f69f1dcbc3)

- AUC-ROC:
    
  ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/b142d007-5ad5-48e6-8b5f-3853ef5c53d2)

- AUC-PR:
    
  ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/bc3fec9c-4625-40f5-9301-a3a3749216ab)


### Предварительная обработка данных
Предварительная обработка данных играет важную роль в успешной построении дерева решений. Этот этап включает в себя:
- Удаление дубликатов: Проверка на наличие дубликатов в данных и их удаление для избежания искажений.
- Обработка пропущенных значений: Заполнение или удаление строк с пропущенными значениями, чтобы не исказить результаты.

  Предварительная обработка данных

  ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/bf668e21-886c-4492-afab-7cd4d7a2d24b)
  ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/6d9ae06f-31d6-4349-a00c-d7019d526ffe)

  
### Построение дерева решений
Был разработан и реализован алгоритм построения дерева решений без использования сторонних библиотек, за исключением NumPy и Pandas. Этот алгоритм принимал на вход отобранные признаки и классифицировал грибы на съедобные и несъедобные на основе значений признаков. Для этого использовался подход "сверху вниз" с выбором наилучшего признака для разделения данных на каждом уровне дерева. Этот процесс включал в себя расчет прироста информации и энтропии для определения наилучшего разделения.

- Отбор признаков для составления дерева решений

  ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/8c0981a5-4069-46b9-a6f9-c38fb0807772)

- Результат выполнения обучения и предсказания

  ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/e3b9faf1-51b3-4e4a-b519-e22360db8584)

- Результаты:

  1. При отобранных признаках (gill-size, stalk-color-above-ring, cap-shape, gill-attachment):
     
    ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/3b9be2ab-fbd6-4521-8335-055d3bbd7a17)

  2. При отобранных признаках (habitat, gill-color, stalk-surface-below-ring, gill-attachment):
     
     ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/df58fca0-1cca-479b-9394-9a80f57cb4ff)

В ходе выполнения лабораторной работы был разработан алгоритм построения дерева решений без использования сторонних библиотек для задачи классификации грибов.. Также было проведен случайный отбор sqrt(n) признаков из датасета.

Реализованный алгоритм был оценен с использованием метрик Accuracy, precision и recall. Accuracy позволяет оценить общую точность классификации, precision измеряет точность положительных предсказаний, а recall измеряет способность модели обнаруживать все положительные случаи.

Кроме того, были построены кривые AUC-ROC и AUC-PR. AUC-ROC отражает способность модели разделять положительные и отрицательные классы в различных пороговых значениях, тогда как AUC-PR показывает, как хорошо модель распознает положительные классы при изменении пороговых значений.

Результаты оценки и визуализации показали, что разработанный алгоритм способен эффективно выполнять поставленную задачу.

### Функции
В коде определены функции, которые выполняют следующие действия:
  - Расчет информационной энтропии для набора данных, чтобы оценить неопределенность в данных.
  - Разделение набора данных на поднаборы по определенному признаку и его значению.
  - Выбор наилучшего признака для разделения данных на основе прироста информации.
  - Определение класса с наибольшей частотой в списке классов.
  - Генерация дерева решений на основе входных данных, выбора наилучшего признака и рекурсивного построения дерева.
  - Классификация класса для одного экземпляра данных на основе построенного дерева.
  - Расчет точности (Accuracy), точности (Precision) и полноты (Recall) для оценки производительности классификации.
  - Построение кривых AUC-ROC (Receiver Operating Characteristic) и AUC-PR (Precision-Recall) для визуализации качества классификации.
    
### Оценка производительности

Для оценки производительности построенного дерева решений использовались следующие метрики:
- Accuracy: Позволяет оценить общую точность классификации. Эта метрика измеряет долю правильно классифицированных грибов относительно общего числа грибов.
- Precision: Измеряет точность положительных предсказаний. Это означает долю правильно классифицированных съедобных грибов относительно всех классифицированных съедобных грибов.
- Recall: Измеряет способность модели обнаруживать все положительные случаи. Это доля правильно классифицированных съедобных грибов относительно всех фактически съедобных грибов.
- AUC-ROC
- AUC-PR
  
Оценка производительности позволяет понять, насколько хорошо построенное дерево решений справляется с задачей классификации грибов на съедобные и несъедобные.

## Примеры использования метода
Метод деревьев решений является мощным инструментом в области машинного обучения и может быть полезен в различных ситуациях. Вот несколько примеров использования метода деревьев решений:
- Классификация медицинских диагнозов: Деревья решений могут использоваться для классификации медицинских диагнозов на основе набора симптомов и тестовых данных. Это позволяет врачам быстро и точно определить диагноз пациента.
- Кредитное скоринг: В финансовой сфере деревья решений могут использоваться для оценки кредитоспособности заемщиков. Алгоритм может учитывать различные факторы, такие как кредитная история, доход, возраст и другие, чтобы принимать решение о выдаче кредита.
- Прогнозирование спроса на товары и услуги: Деревья решений могут использоваться для прогнозирования спроса на товары и услуги в зависимости от различных факторов, таких как сезон, рекламные акции, цены и другие.
- Обнаружение мошенничества: В банковской и финансовой отрасли деревья решений могут использоваться для выявления мошеннических операций. Алгоритм может анализировать транзакции и выявлять аномалии, которые могут указывать на мошенничество.
- Классификация текстовых данных: Деревья решений могут применяться для классификации текстовых данных, таких как отзывы, комментарии или электронные письма. Это полезно, например, для автоматической фильтрации спама или анализа настроений в социальных сетях.

Почему деревья решений выбираются в этих ситуациях?
- Интерпретируемость: Деревья решений относительно легко интерпретировать. Решения, принятые алгоритмом, могут быть объяснены человеку, что важно в медицинских и финансовых приложениях.
- Простота и скорость обучения: Деревья решений обучаются быстро и могут быть применены к большим объемам данных. Это полезно в задачах, где важно получить результаты в реальном времени.
- Устойчивость к выбросам: Деревья решений могут быть устойчивы к выбросам в данных, что важно в сферах, где данные могут быть неточными или зашумленными.
- Автоматизация: Деревья решений могут быть легко автоматизированы и встроены в системы принятия решений.

В целом, метод деревьев решений предоставляет широкий спектр возможностей для решения разнообразных задач классификации и регрессии в различных областях.
