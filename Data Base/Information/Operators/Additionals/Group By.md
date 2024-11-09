Для вычисления суммарных значений на основе данных одной или нескольких таблиц можно использовать предложение GROUP BY, имеющее такой синтаксис:

	GROUP BY {column1} [, …]

Например, следующий запрос связывает две таблицы, сортирует их по полю CustomerID, для каждого значения CustomerID создает одну строку в результирующем наборе данных и вычисляет количество значений поля OrderID для каждого значения CustomerID:

	SELECT Customers.CustomerID,
	
	COUNT (Orders.OrderID)
	
	FROM Customers INNER JOIN Orders
	
	ON Customers.CustomerID = Orders.CustomerID
	
	GROUP BY Customers.CustomerID

В приведенном выше примере запроса мы использовали в предложении SELECT агрегатную функцию COUNT, вычисляющую количество значений. В [табл. 10](http://www.compress.ru/Temp/325/tab2.htm) указан список наиболее часто используемых агрегатных функций.

Помимо перечисленных выше агрегатных функций можно использовать также математические и строковые функции, приведенные в [табл 11](http://www.compress.ru/Temp/325/tab3.htm).