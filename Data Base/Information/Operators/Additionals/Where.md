#### Предложение WHERE

Для фильтрации результатов, возвращаемых оператором SELECT, можно использовать предложение WHERE, синтаксис которого имеет вид:

	WHERE expression1 [{AND | OR} expression2 […]]

Например, вместо получения полного списка продуктов можно ограничиться только теми из них, у которых значение поля CategoryID равно 4:

	SELECT * FROM Products
	
	WHERE CategoryID = 4

В предложении WHERE можно использовать различные выражения, например:

	SELECT * FROM Products
	
	WHERE CategoryID = 2 AND SupplierID > 10

или:

	SELECT ProductName, UnitPrice FROM Products
	
	WHERE CategoryID = 3 OR UnitPrice < 50

или:

	SELECT ProductName, UnitPrice FROM Products
	
	WHERE Discontinued IS NOT NULL

Выражение ‘IS NOT NULL’ означает, что соответствующая колонка результирующего набора данных не может содержать пустых значений.

В предложении WHERE можно использовать один из шести операторов отношений, определенных в SQL. Эти операторы приведены в таблице:

![[binary operators.png]]


Помимо перечисленных выше простых операторов сравнения, можно использовать и специальные операторы сравнения, приведенные в таблице:

![[compare operators.png]]

Приведем несколько примеров применения этих операторов. Для сопоставления данных с маской применяется ключевое слово LIKE:

	SELECT CompanyName, ContactName
	
	FROM Customers
	
	WHERE CompanyName LIKE ‘M%’

В данной маске символ ‘%’ (процент) заменяет любую последовательность символов, а символ '_' (подчеркивание) — один любой символ. Тот же самый результат может быть получен следующим способом:

	SELECT CompanyName, ContactName
	
	FROM Customers
	
	WHERE CompanyName BETWEEN ‘M’ AND ‘N’

В последнем примере мы можем расширить область поиска. В частности, при поиске компаний с именами, начинающимися с букв от A до C, можно выполнить следующий оператор SELECT:

	SELECT CompanyName, ContactName
	
	FROM Customers
	
	WHERE CompanyName BETWEEN ‘A’ AND ‘D’

Используя оператор LIKE, мы можем сузить диапазон поиска, применив более сложную маску для сравнения. Например, чтобы найти компании, содержащие в своем названии подстроку bl, можно применить следующий запрос:

	SELECT CompanyName, ContactName
	
	FROM Customers
	
	WHERE CompanyName LIKE ‘%bl%’

Маска ‘%bl%’ показывает, что до и после искомой подстроки может быть любое количество произвольных символов.

Используя оператор IN, можно задать список значений, в котором должно содержаться значение поля:

	SELECT CompanyName, ContactName
	
	FROM Customers
	
	WHERE CustomerID IN (‘ALFKI’, ‘BERGS’, ‘VINET’)