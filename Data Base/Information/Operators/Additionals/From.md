#### Предложение FROM

Для указания имен таблиц, из которых выбираются записи, применяется ключевое слово FROM, например:

	[SELECT * FROM Customers

Этот запрос возвратит все поля из таблицы Customers.

Если в результирующем наборе данных нужны только поля CompanyName и ContactName, мы можем ввести следующее предложение SELECT:

	SELECT CompanyName, ContactName FROM Customers]

Пример запроса к более чем одной таблице приведен ниже:

	SELECT Customers.CompanyName, Shippers.CompanyName
	
	FROM Customers, Shippers