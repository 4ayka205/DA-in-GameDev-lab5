# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #5 выполнил(а):
- Быкова Екатерина Владимировна
- РИ-230910

Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

## Цель работы
Познакомиться с программными средствами для создания системы машинного обучения и ее интеграции в Unity.

## Задание 1
### Найдите внутри C# скрипта “коэффициент корреляции ” и сделать выводы о том, как он влияет на обучение модели.

Я считаю, что в данном контексте коэффициентом корреляции будет выступать максимальное расстояние, на которое агент должен удалиться от цели. В исходном скрипте это значение составляет 1.42. Иными словами, это величина, которая позволяет сравнить ожидаемый результат от агента и его итоговый результат в процессе обучения.

Вот как выглядит логирование при начальных значениях:
![task 1](https://github.com/4ayka205/DA-in-GameDev-lab5/blob/main/img/photo_2024-12-18_21-33-58.jpg?raw=true)

Если увеличить максимальное расстояние до 3, то значение среднего вознаграждения увеличивается и остаётся на уровне, близком к единице. Однако результаты обученной модели не являются удовлетворительными: шарик может не достичь кубика, но при этом будет засчитан как попадание. 

Вот как выглядит логирование при увеличенном максимальном расстоянии:
![task 1](https://github.com/4ayka205/DA-in-GameDev-lab5/blob/main/img/photo_2024-12-19_00-18-12.jpg?raw=true)

Если уменьшить максимальное расстояние до 1, то увеличивается среднее отклонение от цели. Кроме того, если наблюдать за работой модели, обученной с таким значением, можно заметить, что шарик рядом с кубом начинает кружить и искать нужную точку. Это увеличивает время поиска цели.

Вот как выглядит логирование при уменьшином максимальном расстоянии:
![task 1](https://github.com/4ayka205/DA-in-GameDev-lab5/blob/main/img/photo_2024-12-18_23-38-04.jpg?raw=true)


В заключение можно отметить, что в этой ситуации коэффициент корреляции будет определять, насколько активно агент будет стремиться к достижению цели, минимизируя среднее отклонение от него.
## Задание 2
### Изменить параметры файла yaml-агента и определить какие параметры и как влияют на обучение модели. Привести описание не менее трех параметров.

В процессе обучения агента, при изменении параметра max_steps, происходит модификация максимального количества шагов (итераций), которые агент способен совершить. Уменьшение этого параметра приводит к сокращению времени обучения, однако качество результата обучения существенно снижается.
![task 2](https://github.com/4ayka205/DA-in-GameDev-lab5/blob/main/img/photo_2024-12-19_03-26-30.jpg?raw=true)

Параметр time_horizon, может оказывать значительное влияние на скорость и результативность обучения агента, поскольку он определяет, сколько шагов агент должен принимать во внимание при принятии решений. Однако в данном случае не было зафиксировано существенных изменений.![task 2](https://github.com/4ayka205/DA-in-GameDev-lab5/blob/main/img/photo_2024-12-19_05-13-08.jpg?raw=true)

При изменении количества эпох обучения с 3 на 1 произошло сокращение общего времени обучения, при этом среднее значение вознаграждения возросло. Значения среднего отклонения колеблются. Количество эпох обучения может оказывать влияние на итоговую точность работы модели, однако в данном случае модель не нуждается в большом количестве эпох для обучения, поэтому результат обучения остался удовлетворительным.
![task 2](https://github.com/4ayka205/DA-in-GameDev-lab5/blob/main/img/photo_2024-12-19_06-27-48.jpg?raw=true)

## Задание 3
### Приведите примеры, для каких игровых задачи и ситуаций могут использоваться примеры 1 и 2 с ML-Agent’ом. В каких случаях проще использовать ML-агент, а не писать программную реализацию решения? 

Агента из 1 примера можно использовать в следующих случаях:
- Игры с погоней: Агент, управляющий персонажем, преследующим другого персонажа. В таких играх ML-Agent может научиться эффективно предсказывать траекторию движения цели и выбирать оптимальный путь для ее перехвата.
- Навигация в лабиринте: Агент, управляющий персонажем, должен найти выход из лабиринта, избегая препятствий. ML-Agent может научиться определять кратчайший путь к выходу, используя информацию о своем местоположении и расположении стен.
- Поиск сокровищ: Агент, управляющий персонажем, должен найти спрятанные сокровища на карте. ML-Agent может научиться анализировать карту, находить закономерности в расположении сокровищ и быстро их находить.

Агента из 2 примера можно использоватьв следующих случаях:
- Стратегические игры: Агент, управляющий юнитами в реальном времени, должен собирать ресурсы и создавать новые юниты. ML-Agent может научиться эффективно управлять ресурсами, оптимизировать сбор ресурсов и создавать новые юниты в соответствии с текущей ситуацией.
- Экономические симуляторы:
Агент, управляющий предприятием, должен производить товары, продавать их на рынке и получать прибыль.
ML-Agent может научиться анализировать рыночные данные, оптимизировать производство и управление финансами для максимальной прибыли.
- Сбор ресурсов: Агент, управляющий npc-персонажами, должен собирать ресурсы и выполнять монотонную работу.

Использование ML-агентов может быть более эффективным, когда задача требует адаптивности, обработки больших объемов данных или взаимодействия с динамичной средой, а также когда традиционные алгоритмы оказываются неэффективными или трудозатратными в реализации.

## Выводы

В процессе работы были обучены две различные модели Ml-агентов, каждая из которых выполняла свою задачу: одна — поиск постоянно перемещающейся цели, а другая — перемещение между статическими целями. Для первой модели было создано несколько вариаций с различными конфигурациями обучения, и были проанализированы зависимости результатов от входных параметров.

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
