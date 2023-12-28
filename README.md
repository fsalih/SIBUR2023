# **Sibur Challenge 2023 // Генерализация**

Я в 2023 году участвовал на хакатоне Sibur Challenge 2023 // Генерализация

https://platform.aitoday.ru/event/9

На соревновании я участвовал с младшим братом Забиром, у которого работа связана с базами данных (SQL). Я ему предложил поучаствовать в качестве помошника, и для его развития в области программирования. Его роль была важна как для результативности команды, так и для нас обоих в плане развития. 

## Задача 2
В рамках соревнования участникам предлагается построить ML-модели, которые помогут технологам проводить виртуальные эксперименты.
Нужно решить задачу прогноза количества двух продуктов в зависимости от типа сырья и параметров производственного процесса. 
Обязательное требование - хорошая масштабируемость моделей: адекватные прогнозы для значений признаков, находящихся за границами обучающей выборки. 
Это обусловлено самой идеей цифровых экспериментов: проверка нестандартных кейсов, для которых статистических данных мало или они отсутствуют вовсе.

Выкладываю решения, которые я пробовал. 

**Результативность на соревновании 48/164.**

## История моего участия
Это мое второе участие в хакатоне и первое, когда я уже обладал достаточными знаниями, для решения задач машинного обучения (самым первым был MTS ML CUP, когда я только начинал изучать DS).
К моменту начала соревнования в изучении DataScience я дошел до темы Deployment. Т.е. прошел в sklearn линейные модели, деревья и леса решений, базовые нейронные сети и методы обработки и подготовки данных.
Другие модели изучал и применял так сказать "на ходу". Это методы балансировки, кластеризации, библиотеки pytorch, keras, autokeras, работу с графическим процессором. Про кросс валидацию, регуляризацию и пайплайны еще не знал.
### Этап 1 - Ознакомление с задачей
После проверки бейзлайна решил сразу проверить обычную нейронную сеть (с функцией активации RELU), уж очень хотелось побыстрее попробовать :)). Вначале получилось достаточно внушительно, даже попал в первую десятку (в силу того, что все еще только начиналось). Но вскоре стало ясно, что надо подробно изучить данные и что-то с этим делать.
### Этап 2 - Визуализация и анализ
Начался анализ данных, различные визуализации, подбор фич, подбор подходов. Делая обзор по прошествии полугода, понятно, что отсутствие каких-то знаний и подходов было осложняющим фактором, но тем не менее поиск различных вариантов решений проводился и достаточно хорошо. Понятно, что анализ и визуализация проводилась в течение всего участия на хакатоне, но его я выделил в отдельный блок, так же как и отдельный ноутбук для этих целей.
### Этап 3 - Техническая сторона
Для решения у меня было время только после работы и примерно 2 - 4 часа в день. Идей до последних дней хакатона было достаточно много, поэтому требовалось как-то их реализовывать и быстро просчитывать. Поскольку я основную ставку сделал на нейросети, то соответственно требовалось много времени для их расчета. И я решая задачи хакатона параллельно продумывал разные варианты ускорения расчетов. В основном расчеты я проводил на своем игровом ноутбуке. Также пробовал Google Colab, но на ночь его я не мог оставить, а вариант сохранения результатов как-то не продумал тогда (хотя можно было на диск сохранять). Также пробовал Yandex Data Sphere, но там как раз к этому времени грант был исчерпан, а тратить деньги на него не очень-то хотелось. Хотя в крайний день хакатона все же потратил около 500 рублей для ускорения расчетов. Поскольку мой ноут игровой (покупал его для расчетов гидродинамической модели), то в нем есть и графический процессор (NVIDIA GEFORCE GTX 1050). Решил попробовать на нем проводить расчеты. Но для проведения расчетов на нем все же пришлось поиграть "танцы с бубном" :) После всех этих попыток ускорения работы пришел к выводу, что мне нужна помощь. Какое счастье, что есть брат, готовый помочь, умеющий программировать и готовый учиться. 
### Этап 4 - Я теперь учитель
Я быстро ввел Забира в курс дела: объяснил решаемую задачу, провел обзор методов машинного обучения а-ля "напиши свою нейросеть за 3 вечера с нуля". Дал потренироваться с бейзлайном. Также вместе с ним провели "танцы с бубном" для подключения графического процессора. А дальше он самостоятельно проводил расчеты по идеям, которые я ему закидывал для решения. Сабмиты в основном делал я опираясь на метрики моделей. Да, еще один нюанс, вся коммуникация между нами была в удаленном формате по whatsapp и telegram - работать в офлайн формате не было времени. 
### Этап 5 - Идея -> Реализация -> Расчет -> Оценка -> Корректировка -> Сабмит -> Следующая идея
Примерно так выглядел цикл работы. Иногда для одной идеи были несколько сабмитов с различными вариациями.  От тактик победителей хакатона конечно отличается - у них сразу был выбран победный вариант а дальше этот вариант дотачивался (но это мой взгляд на них). 
### Использованные подходы и идеи
1. Возведение в степень, логарифмирование, потенциирование - по-моему эта идея была у всех и она улучшала результативность. Организаторы сразу сказали, что зависимые от времени переменные считать отсутствующими или выданными в виде фичи (наверно, чтобы не мучались с дифференцированием). Я не знал про полиномиальный трансформер, и вообще про существование трансформеров (кроме OHE и скалеров). Полиномиальный трансформер мог упростить создание фич и улучшении результата (2е место использовал его).
2. При просмотре гистограмм по фичам видно, что большинство из них имеют многомодальное распределение. Поэтому попробовал фичи делать дискретными, но особых успехов в этом направлении не получил. Зато узнал что такое K-Means, метод локтя (почему-то хочется сказать метод колена) и метод силуэта.
3. В зависимости target1 от target0 можно разглядеть квадратичную зависимость. Пробовал использовать это в качестве улучшения результативности последовательно сначала определяя target0, а потом использовать его при определении target1. Но это тоже не дало результатов.
4. Также многие заметили, что фича gas имеет значительное влияние на результат. Но я не смог реализовать это знание в результат, а надо было строить для каждого из них отдельную модель (у второго места так, а у первого все в одной модели, но первое место это отдельная тема для изучения).
5. Аналогичная история с feature8, там в данных заметил разделение по значению -40. Но прироста результативности не получил.
6. В поисках узнал sns.pairplot и hue='feature'. Штука весьма полезная, сейчас я ее часто использую.
7. Самая явная зависимость таргета была от feature13. В попытках использования этой информации писал свои функции-трансформеры для получения новых фич, ну и попутно примял для других  фич. Вот тут бы мне и помогло знание L1 и L2 регуляризации.
8. Самым важным улучшением было использование подхода, названным мной "балансировка". Суть в том, чтобы многомодальное распределение данных было более равномерным. Смог я его сделать с помощью RandomOverSampler, сделав таргет дискретным. Возможно тут сработал эффект того, что каждый таргет предсказывался отдельной моделью, а возможно, сработала "балансировка".
9. 

### Продолжение в разработке...



