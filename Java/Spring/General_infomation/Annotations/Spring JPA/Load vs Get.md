Get - делает обращение к БД и выдаёт результат в виде объекта

Load - **НЕ** делает запрос к БД и возвращает так называемый Proxy объект ('Proxy' объект - объект того же класса, но все поля null, кто id). Но если вызвать геттер на любом из полей, то тогда будет сделан запрос к БД и достанутся значения всех полей. Проще говоря Load - ленивый Get

	Session session = sessionFactory.getCurrentSession();
	Person personProxy = sesson.load(Person.class, id);

### Когда же полезен Load?

Например можно через load загрузить Person в объект Item. Таким образом мы немного оптимизировали запрос.

	Item item = new Item("Some new item");
	Person personProxy = session.load(Person.class, id);
	item.setOwner(personProxy);
	session.save(item);

В данном примере возможна проблема, что человека с таким id просто не существует, но в таком случае мы не сможем сделать владельца с несуществующим id из-за foreign key в таблице Item.

