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
