# Лабораторная работа №3. Разработка системы поддержки принятия решения на основе базы знаний или онтологии

Целью этой лабораторной работы является разработка программы, которая будет использовать базу знаний или онтологию для предоставления рекомендаций на основе введенных пользователем данных.

## Задание

- Создать программу, которая позволяет пользователю ввести запрос через командную строку. Например, информацию о себе, своих интересах и предпочтениях в контексте выбора видеоигры - на основе фактов из БЗ/Онтологии.
- Использовать введенные пользователем данные, чтобы выполнить логические запросы к  БЗ/Онтологии.
- На основе полученных результатов выполнения запросов, система должна предоставить рекомендации или советы, связанные с выбором из БЗ или онтологии.

## Пример

### Входная строка:

Мне 13 лет, мне нравятся: RPG, инди-игры

### Нужно:

Спарсить строку, разбить на факты, построить запрос, используя эти предикаты. (Формат входной строки фиксированный, искать частичное соответсвие подстроки не нужно)

## Критерии оценки:

- Корректность и эффективность реализации системы поддержки принятия решения.
- Способность программы адекватно использовать базу знаний или онтологию для выдачи рекомендаций.
- Качество тестирования и обработка ввода пользователя.
- Качество документации и описание работы системы.

## Реализация

Реализация доступна [здесь](https://github.com/ITSamantha/Artificial_Intelligence_Systems/tree/main/module1/lab3).

### Общая информация о проеке assassins:

|           Характеристика           |                       Реализация                        |
|:----------------------------------:|:-------------------------------------------------------:|
|           Тип приложения           |                       Консольное                        |
|       Язык программирования        |                         Python                          |
| Библиотека для работы с онтологией | [owlready2](https://owlready2.readthedocs.io/en/v0.44/) |

### Демонстрация работы приложения

|       Скриншот работы программы        |                 Действие                  |
|:--------------------------------------:|:-----------------------------------------:|
| ![image](https://github.com/ITSamantha/Artificial_Intelligence_Systems/assets/100091168/61a917a0-f4ba-465d-a8c4-b2f546677bc3)| Запуск, приветствие и приглашение к вводу |
| ![image](https://github.com/ITSamantha/Artificial_Intelligence_Systems/assets/100091168/2108a387-16ee-420b-bc59-1c9041f5bc37)|          Неверный формат строки           |
| ![image](https://github.com/ITSamantha/Artificial_Intelligence_Systems/assets/100091168/b467accd-1edb-4cd7-a879-6123e379648e)|                 Ввод жанров               |
| ![image](https://github.com/ITSamantha/Artificial_Intelligence_Systems/assets/100091168/07a1afa3-02c0-45b6-b18b-3b8960f8f9f8)|                Ввод главного героя        |
| ![image](https://github.com/ITSamantha/Artificial_Intelligence_Systems/assets/100091168/4f569f44-4713-4f25-9ba3-997715474699)|                   Ввод механик            |
| ![image](https://github.com/ITSamantha/Artificial_Intelligence_Systems/assets/100091168/796bdd75-8aa0-4708-b717-1194b45df37f)|                    Ввод типов             |
| ![image](https://github.com/ITSamantha/Artificial_Intelligence_Systems/assets/100091168/98c6d85a-83e0-461e-a89f-b29b00e010f2)|                  Ввод лимита возраста     |
 | ![image](https://github.com/ITSamantha/Artificial_Intelligence_Systems/assets/100091168/1bd395ab-9593-4bfd-9144-66c492d66fd9)|                     Ввод рейтинга         |
 | ![image](https://github.com/ITSamantha/Artificial_Intelligence_Systems/assets/100091168/c5c46e1b-d6d6-464a-b08f-cac1ee57d836)|                    Ввод года выпуска      |
| ![image](https://github.com/ITSamantha/Artificial_Intelligence_Systems/assets/100091168/fb5bbb85-d95b-48d1-a715-9617347975be)|                      Результат            |

## Вывод
В ходе работы я научилась оперировать средствами онтологий (.owl, .rdf файлами) в Python: осуществлять запросы на проверку/поиск/обнаружение фактов. Моя система способна помогать человеку в подборе видеоигры.
