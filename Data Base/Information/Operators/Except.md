Оператор **EXCEPT** в PostgreSQL позволяет найти разность двух выборок, то есть те строки которые есть в первой выборке, но которых нет во второй. Для его использования применяется следующий формальный синтаксис:

	SELECT_выражение1
	
	EXCEPT
	
	SELECT_выражение2

Пример:

Надо найти всех клиентов банка, которые не являются его сотрудниками:

	SELECT FirstName, LastName FROM Customers  
	EXCEPT  
	SELECT FirstName, LastName FROM Employees;