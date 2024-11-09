### Оператор UPDATE

Для изменения значений в одной или нескольких колонках таблицы применяется оператор UPDATE. Синтакcис этого оператора имеет вид:

	UPDATE tableSET column1 = expression1 [, column2 = expression2] [,…]
	
	[WHERE criteria]

Выражение в предложении SET может быть константой или результатом вычислений. Например, для повышения цен всех продуктов, стоящих меньше 10 долл., можно выполнить следующий запрос:

Примеры:

	UPDATE Products
	
	SET UnitPrice = UnitPrice * 1.1
	
	WHERE UnitPrice < 10

  

	UPDATE Salespeople
	
	SET sname = 'Gibson',city = 'Boston',comm = .10
	
	WHERE snum = 1004;

  

	UPDATE Salespeople
	
	SET comm = comm * 2
	
	WHERE city = 'London';