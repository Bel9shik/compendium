Объект для взаимодействия с Hibernate. Когда хотим что-то делать с БД через Hibernate - получаем сессию. Объект Session получаем из объекта SessionFactory

	SessionFactory sessionFactory = new Configuration().configure().buildSessionFactory();  
	Session session = sessionFactory.openSession();

На объекте Session можно вызывать:
* save
* update
* get
* ...

 