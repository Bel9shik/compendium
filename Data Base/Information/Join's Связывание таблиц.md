Как мы уже убедились, можно создавать запросы, позволяющие извлечь данные из нескольких таблиц. Одна из возможностей сделать это заключается в связывании таблиц по одному или нескольким полям. Обратите внимание на то, что без связывания таблиц в результате запроса получится набор данных, содержащий все возможные комбинации строк каждой из исходных таблиц (известное также как декартово произведение):

	SELECT ProductName, CategoryName
	
	FROM Products, Categories

в то время как запрос, показанный ниже, приводит к отображению списка продуктов с указанием, к какой категории принадлежит данный продукт:

	SELECT ProductName, CategoryName
	
	FROM Products, Categories
	
	WHERE Products.CategoryID = Categories.CategoryID


#### В общем случае синтаксис для связывания таблиц имеет вид:

	SELECT column-list
	
	FROM table1, table2
	
	WHERE table1.column1=table2.column2


![[Pasted image 20241127154545.png]]
#### Inner join

Существует несколько типов связывания таблиц. Например, следующий оператор SQL осуществляет так называемое внутреннее соединение таблиц (inner join) — в этом случае в результирующем наборе данных содержатся записи, в которых значения в связанных полях совпадают:

	SELECT ProductName, CategoryName
	
	FROM Products INNER JOIN Categories
	
	ON Products.CategoryID = Categories.CategoryID

#### Left outer join

Так называемые внешние соединения (outer joins) позволяют нам включить в результат запроса все строки из одной таблицы и соответствующие им строки из другой таблицы. Например:

	SELECT ProductName, CategoryName
	
	FROM Products LEFT OUTER JOIN Categories
	
	ON Products.CategoryID = Categories.CategoryID

#### Right outer join

Это было так называемое левое внешнее соединение (left outer join). Существуют также правые внешние соединения (right outer join), возвращающие все строки из второй (то есть правой) таблицы и соответствующие им строки из другой таблицы:

	SELECT ProductName, CategoryName
	
	FROM Products RIGHT OUTER JOIN Categories
	
	ON Products.CategoryID = Categories.CategoryID
	
#### Full outer join

Комбинируя левое и правое внешние соединения, можно получить полное внешнее соединение, возвращающее все данные из обеих таблиц:

	SELECT ProductName, CategoryName
	
	FROM Products FULL OUTER JOIN Categories
	
	ON Products.CategoryID = Categories.CategoryID

Для получения всех комбинаций строк из обеих таблиц (декартова произведения) можно использовать ключевое слово CROSS JOIN без указания связываемых полей:

#### Cross join

	SELECT ProductName, CategoryName
	
	FROM Products CROSS JOIN Categories

Если в запросе используется более трех таблиц, можно иcпользовать вложенные соединения.