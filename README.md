# SQL
SELECT author, title, *// извлечь название, автора
ROUND(IF(author='Булгаков М.А.',price+(price/100*10),IF(author='Есенин С.А.',price+(price/100*5),price)),2) AS new_price *// высчитать конечную стоимость книг Булгакова и Есенина, которые подорожали соответственно на 10% и 5%. округлить результат до сотых.
FROM book; 

SELECT author, title, price *// извлечь автора, название и цену книг, количество которых не превышает 10
FROM book
WHERE amount<10; *// where - оператор условия, записывается после FROM book

SELECT title, author, price, amount
FROM book
WHERE (price < 500 OR price > 600) AND  amount*price >=5000; *// найти название, автора, цену и количество тех книг. цена которых меньше 500 или больше 600, а их суммарная стоимость больше или равна 5000

SELECT title, author
FROM book
WHERE price BETWEEN 540.50 AND 800 AND amount IN (2,3,5,7); *// вывести название и авторов, цена которых находится в интервале от 540ю50 до 800 включительно, и количество или 2. или 3, или 5, или 7  = WHERE price >= 540.50 AND price <= 800 AND amount=2 OR amount=3 OR amount=5 OR amount=7;

SELECT author, title
FROM book
WHERE amount BETWEEN 2 AND 14
ORDER BY author DESC, title; *// Вывести  автора и название  книг, количество которых принадлежит интервалу от 2 до 14 (включая границы). Информацию  отсортировать сначала по авторам (в обратном алфавитном порядке), а затем по названиям книг (по алфавиту).

SELECT title, author
FROM book
WHERE author LIKE '%С.%' AND title LIKE "_% _%"
ORDER BY title ASC; *//Вывести название и автора тех книг, название которых состоит из двух и более слов, а инициалы автора содержат букву «С». Считать, что в названии слова отделяются друг от друга пробелами и не содержат знаков препинания, между фамилией автора и инициалами обязателен пробел, инициалы записываются без пробела в формате: буква, точка, буква, точка. Информацию отсортировать по названию книги в алфавитном порядке.

SELECT amount 
FROM book
GROUP BY amount; *// Отобрать различные (уникальные) элементы столбца amount таблицы book. =
SELECT DISTINCT amount 
FROM book; =
SELECT DISTINCT amount 
FROM book
GROUP BY amount;

SELECT author AS "Автор",COUNT(amount) AS "Различных_книг", SUM(amount) AS "Количество_экземпляров"
FROM book
GROUP BY author; *//Посчитать, количество различных книг и количество экземпляров книг каждого автора , хранящихся на складе.  Столбцы назвать Автор, Различных_книг и Количество_экземпляров соответственно.

SELECT author, MIN(price) AS Минимальная_цена, MAX(price) AS Максимальная_цена, AVG(price) AS Средняя_цена
FROM book 
GROUP BY author; *// Вывести фамилию и инициалы автора, минимальную, максимальную и среднюю цену книг каждого автора . Вычисляемые столбцы назвать Минимальная_цена, Максимальная_цена и Средняя_цена соответственно.

SELECT author, SUM(price*amount) AS Стоимость, ROUND((SUM(price*amount)*18/100)/(1+18/100),2) AS НДС, ROUND(SUM(price*amount)/(1+18/100),2) AS Стоимость_без_НДС
FROM book
GROUP BY author; *//Для каждого автора вычислить суммарную стоимость книг S (имя столбца Стоимость), а также вычислить налог на добавленную стоимость  для полученных сумм (имя столбца НДС ) , который включен в стоимость и составляет k = 18%,  а также стоимость книг  (Стоимость_без_НДС) без него. Значения округлить до двух знаков после запятой. В запросе для расчета НДС(tax)  и Стоимости без НДС(S_without_tax) использовать следующие формулы:

tax= {{S *{ k \over 100}} \over {1+{k\over 100}}},
tax= 

SELECT min(price) AS Минимальная_цена, max(price) AS Максимальная_цена, ROUND(AVG(price),2) AS Средняя_цена
FROM book; *//Вывести  цену самой дешевой книги, цену самой дорогой и среднюю цену уникальных книг на складе. Названия столбцов Минимальная_цена, Максимальная_цена, Средняя_цена соответственно. Среднюю цену округлить до двух знаков после запятой.

Пояснение. В задании нужно посчитать среднюю цену уникальных книг на складе, а не среднюю цену всех экземпляров книг.

SELECT ROUND(AVG(price),2) AS Средняя_цена, ROUND(SUM(amount*price),2) AS Стоимость
FROM book
WHERE amount 
BETWEEN 5 AND 14; *//Вычислить среднюю цену и суммарную стоимость тех книг, количество экземпляров которых принадлежит интервалу от 5 до 14, включительно. Столбцы назвать Средняя_цена и Стоимость, значения округлить до 2-х знаков после запятой.
