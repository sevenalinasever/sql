# SQL
SELECT author, title, 
ROUND(IF(author='Булгаков М.А.',price+(price/100*10),IF(author='Есенин С.А.',price+(price/100*5),price)),2) AS new_price 
FROM book; 
