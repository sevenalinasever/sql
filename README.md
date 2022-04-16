# SQL
SELECT author, title, 
ROUND(IF(author='Булгаков М.А.',price+(price/100*10),IF(author='Есенин С.А.',price+(price/100*5),price)),2) AS new_price 
FROM book; 

SELECT author, title, price *// извлечь автора, название и цену книг, количество которых не превышает 10
FROM book
WHERE amount<10;
