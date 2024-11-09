Используется для того, чтобы можно "слушать" другой объект. И, к примеру, реагировать на изменение какой-то величины у объекта (условно на изменение ширины прямоугольника)

	IntegerProperty a = new SimpleIntegerProperty();  
	a.setValue(100);  
	  
	IntegerProperty b = new SimpleIntegerProperty();  
	b.setValue(200);

Связать два проперти:

	a.bindBidirectional(b);


Теперь изменим значение объекта а на другое значение:

	a.setValue(400);  

И такой вывод в консоли выдаст следующий результат:
  
	System.out.println(a);  
	System.out.println(b);
	
	
	IntegerProperty [value: 400]
	IntegerProperty [value: 400]

### Важно

К [[Property]] можно добавлять листинер

**_Во всех_** объектах UI control можно пользоваться [[Property]]