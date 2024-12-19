## ** _Объединение множеств_ **

Оператор UNION позволяет объединить два множества (условно две таблицы). Но в отличие от inner/outer join объединения соединяют не столбцы разных таблиц, а два однотипных набора в один. Формальный синтаксис объединения:

	SELECT_выражение1
	
	UNION [ALL]
	
	SELECT_выражение 2
	
	[UNION [ALL] SELECT_выражение N]
	

Пример:

	SELECT FirstName, LastName FROM Customers
	
	UNION
	
	SELECT FirstName, LastName FROM Employees;