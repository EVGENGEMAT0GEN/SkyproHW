**Задание 2** 
-------------
<div> <img src="https://media0.giphy.com/media/3oEduHMN7pshESmP5e/giphy.gif?cid=ecf05e47e8zbqkjq82msee5v9tyouy067h8flz20nz3s4tqg&ep=v1_gifs_search&rid=giphy.gif&ct=g" width="40" align="left"/> </div>  
<br>
<br>
<br>
<br>

*Задача* - протестировать методы для работы с видео YouTube.

*Необходимо с помощью Postman протестировать работу следующих методов:*
1. Получить список видео по id jifUJrYPZQQ.
2. Поставить like видео с id jifUJrYPZQQ.
3. Получить список самых популярных видео.

**Типы запросов:**
1. GET на получение списков видео по id jifUJrYPZQQ.
2. POST для того, чтобы поставить like видео.
3. GET gолучения списка самых популярных видео.

Для работы с постман коллекцией использовался метод авторизации APIkey. Ключ получен из личного кабинета.

В качестве проверки успешного прохождения запросов использовалась проверка статус кода: pm.test("Status code is 200", function () { pm.response.to.have.status(200); });
Запросы можно найти в репозитории: файл "Аттестация в ЦК.JSON".

**Тест кейсы:**
1. Получение списка (метод list) видео по id.

*Предусловия:*
Привязать к Google-почте профиль разработчика, получить API Key и Access Token.

*Шаги:*
1. Отправить запрос с методом GET на [URL](https://www.googleapis.com/youtube/v3/search).
2. Получить ответ 200.
3. Сверить ответ с [документацией](https://developers.google.com/youtube/v3/docs/search/list?hl=ru).

OP: Код ответа 200. Содержание ответа совпадает с документацией.

2. Поставить лайк под видео.

*Шаги:* 
1. Отправить запрос с методом POST на [URL](https://www.youtube.com/youtubei/v1/like/like?{{BP}}prettyPrint=false).
2. Получить ответ 200.

OP: Код ответа 200. На странице видео изменилось количество отметок типа "LIKE".

3. Получить список самых популярных видео.

*Шаги:*
1. Отправить запрос с методом POST на [URL](https://www.youtube.com/feed/trending?bp=6gQJRkVleHBsb3Jl).
2. Получить ответ 200.
3. Проверить содержание ответа по [документации](https://developers.google.com/youtube/v3/docs/videoCategories/list?hl=ru).

*OP:*
Код ответа 200. Содержание ответа совпадает с документацией.

**Задание 4** 
-------------
<div> <img src="https://raw.githubusercontent.com/devicons/devicon/55609aa5bd817ff167afce0d965585c92040787a/icons/postgresql/postgresql-original.svg" width="40" align="next"/> </div>

<div> <img src="https://media2.giphy.com/media/dxxmvKRt5ms55sTibm/giphy.gif?cid=ecf05e47t1wdnnfzeif8dk58pjg3niu580qkreyk5sar2cfc&ep=v1_gifs_search&rid=giphy.gif&ct=g" width="150" align="left"/> </div>  
<br>
<br>
<br>
<br>
<br>

*Есть 2 таблицы:*
t1 — данные по заявкам на **подбор кредита**;
t2 — выгрузка банка о **решениях по выдаче кредита**.

*С помощью запросов SQL вычислите:*
1. Количество учеников, обучающихся в каждом университете.
2. Название университета с минимальным рейтингом.
3. Все московские университеты.

*Решение:*
1. SELECT COUNT (STUDENT_ID) AS number_of_students FROM students group by univ_id
   JOIN univ_id.students=univ_id.university
2. SELECT university_name FROM university WHERE rating = (SELECT min(RATING) FROM university)
3. SELECT * FROM university WHERE city LIKE 'Москва'
