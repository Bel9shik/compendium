Предложение HAVING имеет назначение, сходное с предложением WHERE, но используется с агрегатными данными. Например:

	SELECT Customers.CustomerID,
	
	COUNT (Orders.OrderID)
	
	FROM Customers INNER JOIN Orders
	
	ON Customers.CustomerID = Orders.CustomerID
	
	GROUP BY Customers.CustomerID
	
	HAVING COUNT(Orders.OrderID) >= 10

Этот запрос аналогичен предыдущему, но в результирующий набор данных включены только заказчики, разместившие десять или более заказов.