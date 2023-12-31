# Лабораторная работа №6. Деревья решений

Целью данной лабораторной работы является реализация деревьев решений "с нуля" без использования сторонних библиотек, кроме NumPy и Pandas. 

## Задание

1. Датасет с [классификацией грибов](https://archive.ics.uci.edu/ml/datasets/Mushroom).
2. Отобрать **случайным** образом sqrt(n) признаков
3. Реализовать без использования сторонних библиотек построение дерева решений (numpy и pandas использовать можно, использовать списки для реализации  дерева - нельзя)
4. Провести оценку реализованного алгоритма с использованием Accuracy, precision и recall
5. Построить AUC-ROC и AUC-PR (в пунктах 4 и 5 использовать библиотеки нельзя)

### Исходные данные:
В качестве исходных данных был предоставлен датасет с информацией о различных видов грибов и их классификации на съедобные и несъедобные. Датасет включает в себя различные признаки (характеристики грибов) и целевую переменную, которая указывает на классификацию грибов.

## Реализация
### Выполненные шаги:
1. Отбор случайных признаков. Сначала был выполнен случайный отбор признаков из исходного датасета. Для этого была использована техника "sqrt(n)" признаков, где "n" - это общее количество признаков в датасете.
2. Построение дерева решений: Был реализован алгоритм построения дерева решений без использования сторонних библиотек, за исключением библиотеки numpy и pandas.
3. Оценка производительности: Для оценки производительности построенного дерева решений были использованы следующие метрики:
    - Accuracy: Оценивает общую точность классификации.
    - Precision: Измеряет долю правильно классифицированных съедобных грибов относительно всех съедобных грибов.
    - Recall: Измеряет долю правильно классифицированных съедобных грибов относительно всех истинных съедобных грибов.
4. Построение кривых AUC-ROC и AUC-PR: Были построены кривые AUC-ROC и AUC-PR для оценки качества классификации. Кривая AUC-ROC оценивает, насколько хорошо модель разделяет съедобные и несъедобные грибы, а кривая AUC-PR оценивает точность и полноту классификации.

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

## Примеры работы

Ниже расположены возможные варианты использования приложения.

- Описание датасета:

  ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/387ebd1c-3bf8-49cb-8a5f-8d661552fb9b)
  ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/1b18a82c-2e43-4ba7-91fd-8648bde939ff)
  ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/761f2fd8-73fc-4b86-aa25-8848553f7f4c)


- Описание статистики атрибутов:

  ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/54fe0707-d7c1-4e25-bc7b-f2d244ac5c5a)
  ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/ccd727c7-6e77-45bb-91c0-69f69f1dcbc3)


- Предварительная обработка данных

  ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/bf668e21-886c-4492-afab-7cd4d7a2d24b)
  ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/6d9ae06f-31d6-4349-a00c-d7019d526ffe)

- Отбор признаков для составления дерева решений

  ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/8c0981a5-4069-46b9-a6f9-c38fb0807772)


- Результат выполнения обучения и предсказания

  ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/e3b9faf1-51b3-4e4a-b519-e22360db8584)

- Результаты:

  1. При отобранных признаках (gill-size, stalk-color-above-ring, cap-shape, gill-attachment):
     
    ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/3b9be2ab-fbd6-4521-8335-055d3bbd7a17)

  3. При отобранных признаках (habitat, gill-color, stalk-surface-below-ring, gill-attachment):
     
     ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/df58fca0-1cca-479b-9394-9a80f57cb4ff)


### Визуализация данных

  - AUC-ROC:
    
  ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/b142d007-5ad5-48e6-8b5f-3853ef5c53d2)

  - AUC-PR:
    
  ![image](https://github.com/ITSamantha/artificial_intelligence_systems/assets/100091168/bc3fec9c-4625-40f5-9301-a3a3749216ab)


## Вывод
В ходе выполнения лабораторной работы был разработан алгоритм построения дерева решений без использования сторонних библиотек для задачи классификации грибов.. Также было проведен случайный отбор sqrt(n) признаков из датасета.

Реализованный алгоритм был оценен с использованием метрик Accuracy, precision и recall. Accuracy позволяет оценить общую точность классификации, precision измеряет точность положительных предсказаний, а recall измеряет способность модели обнаруживать все положительные случаи.

Кроме того, были построены кривые AUC-ROC и AUC-PR. AUC-ROC отражает способность модели разделять положительные и отрицательные классы в различных пороговых значениях, тогда как AUC-PR показывает, как хорошо модель распознает положительные классы при изменении пороговых значений.

Результаты оценки и визуализации показали, что разработанный алгоритм способен эффективно выполнять поставленную задачу.

## Заключение

Лабораторная работа позволила познакомиться с алгоритмами построения дерева решений и оценки качества классификации на примере датасета с грибами. Реализация алгоритма без использования сторонних библиотек и построение кривых AUC-ROC и AUC-PR предоставили студентам практический опыт в области машинного обучения и анализа данных.
