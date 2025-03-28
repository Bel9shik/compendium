Hibernate - ORM (Object-Relational Mapping) библиотека для Java
До началы работы нужно создать конфигурационный файл (hibernate.properties). 
(Из личных наблюдений - названия таблиц должны быть в нижнем регистре)
Пример:

	# Конфигурация источника данных  
	hibernate.driver_class = org.postgresql.Driver  
	hibernate.connection.url = jdbc.postgresql://localhost:5432/HibernateApp  
	hibernate.connection.username= ...
	hibernate.connection.password= ...
	  
	# Конфигурация самого Hibernate  
	hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect  
	hibernate.show_sql=true  
	hibernate.current_session_context_class=thread

При начале работы Hibernate сам найдёт файл hibernate.properties и подключит оттуда зависимости.

Для начала работы с Hibernate необходимо сначала создать сессию [[Session]]

	Configuration cfg = new Configuration().addAnnotatedClass(Person.class);  
	  
	SessionFactory sessionFactory = cfg.buildSessionFactory();  
	Session session = sessionFactory.getCurrentSession();

Единицей работы с БД является [[Transaction]] 

Для того, чтобы дать понять Hibernate какие у нас есть сущности в базе данных - [[@Entity]] 

Для некоторых задач приходится писать запросы. Для этого в Hibernate используется свой язык запросов - [[HQL]]

## Жизненный цикл

Java объекты-сущности проходят через несколько состояний, когда используется Hibernate
* [[Transient]]
* [[Persistent]] (Managed)
* [[Detached]]
* [[Removed]]

## Каскадирование

Изменение всех данных в других таблицах, связанные с этой таблицей

(например при удалени пользователя - удалить все товары, связанные с этим пользователем)

	@OneToMany (mappedBy = "owner", cascade = CascadeType.PERSIST)  
	private List<Item> items;

### Типы каскадирований:

* [[Persist]]