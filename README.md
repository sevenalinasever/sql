# SQL
SELECT author, title, *// извлечь название, автора
ROUND(IF(author='Булгаков М.А.',price+(price/100*10),IF(author='Есенин С.А.',price+(price/100*5),price)),2) AS new_price *// высчитать конечную стоимость книг Булгакова и Есенина, которые подорожали соответственно на 10% и 5%. округлить результат до сотых.
FROM book; 

SELECT author, title, price *// извлечь автора, название и цену книг, количество которых не превышает 10
FROM book
WHERE amount<10; *// where - оператор условия, записывается после FROM book
