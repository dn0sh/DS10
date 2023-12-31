# DAY 10 – Введение в SQL
## Оглавление
1. [Глава I](#глава-i) \
    1.1. [Преамбула](#преамбула)
2. [Глава II](#глава-ii) \
    2.1. [Общая инструкция](#общая-инструкция)
3. [Глава III](#глава-iii) \
    3.1. [Цели](#цели)
4. [Глава IV](#глава-iv) \
    4.1. [Задание](#задание)
5. [Глава V](#глава-v) \
    5.1. [Сдача работы и проверка](#сдача-работы-и-проверка)

## Глава I
### Преамбула
«Сиквел» или «Эс-кью-эл»? Как правильно произносится аббревиатура SQL? Бывали случаи, когда на собеседовании потенциальным новым сотрудникам отказывали в работе, если они не могли правильно произнести эту аббревиатуру. Поэтому тебе нужно хорошо усвоить, как она правильно произносится.

Аббревиатура SQL первоначально писалась как SEQUEL (Structured English Query Language), но позже выяснилось, что это зарегистрированная торговая марка одной из авиационных компаний. Поэтому авторы этого языка программирования были вынуждены изменить его название. С тех пор используется вариант SQL (Structure Query Language). Одного из разработчиков этого языка программирования [спросили](http://patorjk.com/blog/2012/01/26/pronouncing-sql-s-q-l-or-sequel/), какой вариант произношения является правильным. И вот что он ответил.

_«Поскольку язык изначально назывался SEQUEL, многие люди продолжали произносить его название таким образом даже после того, как оно сократилось до SQL. Оба варианта произношения широко распространены, и оба можно использовать. Что касается «официального» названия: по моему мнению, нужно обратиться к стандарту ISO, согласно которому название этого языка программирования по буквам пишется S-Q-L (и, предположительно, произносится таким же образом).
Спасибо за проявленный интерес!»_

Дональд Чемберлин

Как сказал один из авторов языка, можно использовать оба варианта произношения. S-Q-L — это официальный вариант произношения (предположительно, да?). Что об этом думают другие «эксперты»?

Говорят, что официально аббревиатура MySQL произносится как «Май-эс-кью-эл» (а не «май сиквел»). В то же время в официальной документации Oracle говорится, что правильный вариант произношения — это «Сиквел».

Прежде чем перейти к упражнениям, тебе следует сделать важный выбор: собираешься ли ты использовать вариант «Сиквел» или «Эс-кью-эл»? Неформальный или официальный вариант произношения? Какой из них тебе больше по душе?

## Глава II
### Общая инструкция

Методология Школы 21 может быть не похожа на тот образовательный опыт, который случался с тобой ранее. Её отличает высокий уровень автономии: у тебя есть задача, ты должен её выполнить. По большей части тебе нужно будет самому добывать знания для её решения. Второй важный момент — это peer-to-peer обучение. В образовательном процессе нет менторов и экспертов, перед которыми ты защищаешь свой результат. Ты это делаешь перед таким же учащимися, как и ты сам. У них есть чек-лист, который поможет им качественно выполнить приемку вашей работы.

Роль Школы 21 заключается в том, чтобы обеспечить через последовательность заданий и оптимальный уровень поддержки такую траекторию обучения, при которой ты не только освоишь hard skills, но и научишься самообучаться.

- Не доверяй слухам и предположениям о том, как должно быть оформлено ваше решение. Этот документ является единственным источником, к которому стоит обращаться по большинству вопросов;
- твое решение будет оцениваться другими учащимися;
- подлежат оцениванию только те файлы, которые ты выложил в GIT (ветка develop, папка src);
- в твоей папке не должно быть лишних файлов — только те, что были указаны в задании;
- не забывай, что у вас есть доступ к интернету и поисковым системам;
- обсуждение заданий можно вести и в Slack;
- будь внимателен к примерам, указанным в этом документе — они могут иметь важные детали, которые не были оговорены другим способом;
- и да пребудет с тобой Сила!



## Глава III
### Цели
Иногда необходимость использования только одного языка программирования Python значительно ограничивает твои возможности. 
В этом проекте ты будешь работать с языком SQL. В каких случаях его стоит использовать? Иногда данные могут 
храниться не в привычных форматах CSV или JSON, а в формате базы данных, и требуется какой-то инструмент для их 
извлечения. Мы поможем погрузиться в этот язык, используя уже знакомые вам Jupyter Notebooks и Pandas. 
Оказывается, в нем есть и такие возможности.

## Глава IV
В этом проекте снова создай для каждого упражнения отдельную папку: `task1`, `task2`, `task3` и т.д. 
Ведите работу в них.

Скачай [базу данных SQLite](datasets/checking-logs.sqlite). В рамках этого проекта ты будешь работать с различными 
таблицами из этой базы данных, используя библиотеку Pandas. Все упражнения связаны между собой и относятся 
к одному и тому же проекту. Он содержит реальный датасет одной компании из сферы образования. 
В этой компании есть своя платформа, на которой каждый учащийся может проверить правильность своего решения и 
получить некоторую обратную связь на свой ответ. В таблице `checker` хранятся записи о том, когда и какие лабораторные 
задания были выполнены пользователями платформы.

Компания решила создать на платформе новую страницу с лентой новостей, с помощью которой доступ к этим логам 
(кто, когда и какие задания сделал) могут получить все учащиеся в рамках программы. 
Записи о посещениях страницы хранятся в другой таблице с именем `pageviews`. 
Изначальная идея заключалась в том, что при просмотре этой страницы у учащихся возникнет чувство соперничества, 
и они раньше приступят к работе над лабораторными заданиями. Это было бы полезно, поскольку таким образом учащиеся 
могли бы выполнить больше попыток и опробовать при этом разные подходы. В этой серии упражнений ты попытаешься выяснить,
удалось ли реализовать эту идею на практике. И подтвердилась ли эта гипотеза в эксперименте, где одним пользователям 
была показана эта страница, а другим – она не была показана.

![](misc/images/platform.png)


### Task 1
Давай начнем с самого простого. В этом упражнении тебе необходимо получить отфильтрованные данные из таблицы 
в базе данных. Почему важно фильтровать данные именно в запросе, а не после этого в библиотеке Pandas?
Потому что таблицы могут иметь огромный размер. Если ты попыташься получить всю таблицу, то не сможешь ее "переварить" 
– у тебя может не хватить оперативной памяти. Всегда помни об этом.

Первый способ фильтрации — выбрать только те столбцы, которые тебе действительно нужны. 
Второй способ — выбрать только те строки, которые тебе действительно нужны.

Подробное описание задания:

1. Помести базу данных в подкаталог data в корневом каталоге, используемом в рамках этого проекта.
2. Создай соединение с базой данных с помощью библиотеки `sqlite3`.
3. Получи схему таблицы `pageviews` с помощью `pd.io.sql.read_sql` и запроса `PRAGMA table_info(pageviews);`.
4. Получи только первые `10` строк таблицы `pageviews`, чтобы проверить, как она выглядит.
5. Получи подтаблицу с помощью только **одного** запроса, в котором:
    - используются только `uid` и `datetime`;
    - используются только данные пользователей (`user_*`), и не используются данные администраторов;
    - сортировка выполняется по `uid` в порядке возрастания;
    - столбец индекса — это `datetime`;
    - `datetime` преобразован в `DatetimeIndex`;
    - имя датафрейма — `pageviews`.
6. Закрой соединение с базой данных.

### Task 2
А теперь давай усложним задачу.Ты знаешь, что такое подзапрос? Это как запрос, но только внутри запроса. 
Чем он может быть полезен? Например, с его помощью можно сделать определенную агрегацию для выбранных данных. 
Однако следует помнить, что в первую очередь выполняются вложенные запросы, и только после этого — основной запрос.

Что тебе нужно сделать:

1. Создай соединение с базой данных с помощью библиотеки sqlite3.
2. Получи схему таблицы `checker`.
3. Получи только первые `10` строк таблицы `checker`, чтобы проверить, как она выглядит.
4. Подсчитай, сколько строк удовлетворяют следующим условиям, используя только **один** запрос с любым количеством подзапросов.
    - Подсчитай количество строк из таблицы `pageviews`, но только с пользователями из таблицы `checker`, у которых:
        - `status = 'ready'` (мы не хотим анализировать логи со статусом `checking`);
        - `numTrials = 1` (мы хотим проанализировать только первые коммиты, поскольку только они информируют о том, когда студент начал работать над лабораторным заданием);
        - названия лабораторных заданий должны быть только из следующего списка: `laba04`, `laba04s`, `laba05`, `laba06`, `laba06s`, `project1`. Только они были активными во время проведения эксперимента.
    - Сохрани их в датафрейме `checkers` в столбце `cnt`. Датафрейм будет представлять собой только одну ячейку.
5. Закрой соединение.

### Task 3
В этом упражнении ты создашь так называемую витрину данных. Она представляет собой таблицу, 
которую можно использовать для аналитических целей. Обычно она создается путем объединения нескольких отдельных таблиц. 
В этом упражнении мы будем собирать различные данные о наших пользователях: когда они сделали свои первые коммиты, 
когда они впервые посетили ленту новостей и т. д. Это поможет позднее выполнить анализ данных.

Что тебе нужно сделать в этом упражнении (ознакомься с полным описанием задания):

1. Создай соединение с базой данных с помощью библиотеки `sqlite3`.
2. Создай новую таблицу `datamart` в базе данных, объединив таблицы `pageviews` и `checker` с помощью только **одного** запроса.
    - Таблица должна содержать следующие столбцы: `uid`, `labname`, `first_commit_ts`, `first_view_ts`.
    - `first_commit_ts` — это просто новое имя для столбца `timestamp` из таблицы `checker`; он показывает первый коммит конкретного лабораторного задания конкретного пользователя.
    - `first_view_ts` — первое посещение пользователем из таблицы `pageviews`, метка времени посещения пользователем ленты новостей.
    - По-прежнему нужно использовать фильтр `status = 'ready'`.
    - По-прежнему нужно использовать фильтр `numTrials = 1`.
    - Имена лабораторных заданий по-прежнему должны быть из следующего списка: `laba04`, `laba04s`, `laba05`, `laba06`, `laba06s`, `project1`.
    - Таблица должна содержать только пользователей (`uid` с `user_*`), а не администраторов.
    - `first_commit_ts` и `first_view_ts` должны быть распарсены как `datetime64[ns]`.
3. Используя методы библиотеки Pandas, создай два датафрейма: `test` и `control`.
    - `test` должен включать пользователей, у которых имеются значения в `first_view_ts`.
    - `control` должен включать пользователей, у которых отсутствуют значения в `first_view_ts`.
    - Замени пропущенные значения в `control` средним значением `first_view_ts` пользователей из `test` (оно пригодится нам для анализа в будущем).
    - Сохрани обе таблицы в базе данных (вы будете использовать их в следующих упражнениях).
4. Закрой соединение.

Небольшой совет — выполняй все операции поочередно, от простой к более сложной, а не пытаясь сделать всё вместе и сразу. Это поможет в отладке твоих запросов.

### Task 4
На предыдущих этапах ты занимался просто подготовкой данных. Ты не получил никакой аналитической информации на основе имеющихся данных. Пришло время приступить к анализу. Помни, что, согласно нашему предположению, пользователи приступили бы к работе над лабораторными заданиями раньше, если бы они просмотрели ленту новостей? Это означает, что ключевой метрикой для нас является период времени (delta) между датой начала работы пользователя над лабораторным заданием (первого коммита) и сроком сдачи лабораторного задания. Мы будем смотреть на то, меняется ли она в зависимости от просмотра страницы.

Что тебе нужно сделать в этом упражнении:

1. Создай соединение с базой данных с помощью библиотеки `sqlite3`.
2. Получи схему таблицы `test`.
3. Получи только первые `10` строк таблицы `test`, чтобы проверить, как она выглядит.
4. Найди среди всех пользователей минимальное значение этой самой дельты (периода времени от даты первого коммита
пользователя до срока сдачи соответствующего лабораторного задания), используя только один запрос.
    - Для этого сджойни данные своей таблицы с данными таблицы `deadlines`.
    - Период времени должен отображаться в часах.
    - Не учитывай лабораторное задание `project1` с более длительным сроком сдачи, поскольку оно будет выделяться на фоне других.
    - Сохрани значение в датафрейме `df_min` с соответствующим `uid`.
5. Выполни те же самые операции для максимального значения дельты, используя только **один** запрос. Название итогового датафрейма — `df_max`.
6. Выполни те же самые операции для среднего значения дельты, используя только один запрос. На этот раз ваш итоговый датафрейм не должен включать столбец `uid`; имя датафрейма — `df_avg`.
7. Мы хотим проверить предположение о том, что у пользователей, посетивших ленту новостей всего несколько раз, период времени между датой первого коммита и сроком сдачи лабораторного задания меньше. Для этого тебе необходимо рассчитать коэффициент корреляции между количеством просмотров страниц и разницей между датами.
    - Используя только **один** запрос, создай таблицу со столбцами: `uid`, `avg_diff`, `pageviews`.
        - `uid` — это uid, существующие в таблице `test`.
        - `avg_diff` — среднее значение дельты (периода времени между датой первого коммита и сроком сдачи лабораторного задания) для каждого пользователя.
        - `pageviews` — количество посещений ленты новостей одним пользователем.
    - Не учитывай лабораторное задание `project1`.
    - Сохрани результаты в датафрейме `views_diff`.
    - Используй метод `corr()` библиотеки Pandas для вычисления коэффициента корреляции между количеством просмотров и значением дельты.
8. Закрой соединение.


### Task 5
Итак... давай, наконец, выясним, повлияло ли посещение ленты новостей на поведение учащихся. 
Приступили ли они в итоге к работе над лабораторным заданием раньше? Помни, что у нас есть две подготовленные 
таблицы в базе данных: `test` и `control`. Мы выполним нечто, похожее на A/B-тестирование.
Чтобы обнаружить эффект, нам нужно вычислить значение дельты (период времени между датой первого коммита и
сроком сдачи лабораторного задания) до того момента, когда учащиеся впервые посетили страницу с лентой новостей, и после этого.
Мы должны сделать то же самое и для контрольной группы.

Другими словами, каждый пользователь из тестовой таблицы имеет свою собственную временную метку для
первого посещения новостной ленты. Мы хотим вычислить среднее значение дельты 
(разницу между датой первого коммита и сроком сдачи) до этой временной метки и после нее. 
Мы сделаем то же самое для пользователей в контрольной группе. Ты можешь сказать: «Но они вообще не посещали ленту новостей». 
Это так, и ранее мы решили использовать среднюю временную метку первого просмотра пользователями тестовой группы для пользователей контрольной группы.

Если значение дельты перед первым посещением ленты новостей значительно отличается от этого показателя после первого 
посещения в тестовой группе, и мы не видим аналогичного эффекта в контрольной группе, значит, создание страницы 
с новостной лентой было отличной идеей. Мы можем распространить эту практику на всю группу.


Подробное описание:
1. Создай соединение с базой данных с помощью библиотеки `sqlite3`.
2. Используя только **один** запрос для каждой из групп, создай два датафрейма: `test_results` и `control_results` со столбцами `time` и `avg_diff` и только двумя строками.
    - `times` должно иметь значения `before` и `after`.
    - `avg_diff` содержит среднее значение дельты для всех пользователей за период времени до первого посещения ленты новостей каждым из них и после этого.
    - Учитываются только те пользователи, для которых имеются наблюдения и `before`, и `after`.
3. Мы по-прежнему не используем лабораторное задание 'project1'.
4. Закрой соединение.
5. Дайте ответ: оказалось ли предположение верным и влияет ли наличие страницы с новостной лентой на поведение учащихся?

## Глава V
### Сдача работы и проверка

1. Работу над каждым заданием выполняй в отдельном ноутбуке, поскольку объем кода и данных может быть большим. 
Для тебя и проверяющих это будет удобнее.
2. Для каждой основной подзадачи в списке любого упражнения (пронумерованы) файл ipynb должен иметь заголовок уровня 
h2, чтобы другие участники курса могли без проблем разобраться в твоем программном коде.
3. Под каждое упражнение должна быть отдельная папка, в которую входит ноутбук и сохраненные по итогам работы файлы, если таковые были указаны.
4. Загрузи все эти папки на Git в ветку develop.
5. На этом проекте разрешено использовать только следующие методы из библиотеки Pandas: `io.sql.read_sql` и `to_sql` (если иное явно четко не оговорено в упражнении).

💡 [Нажми здесь](https://forms.gle/rXmPtdc4qqcPvfFs7) **чтобы отправить обратную связь по проекту**.  
