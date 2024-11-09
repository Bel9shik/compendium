
![[DispatcherServlet.png]]

  Начиная с 3 версии Spring Framework можно использовать Java-код вместо web.xml

	Для этого необходимо в проекте создать Java класс, который реализует интерфейс org.springframework.web.WebApplicationInitializer

	Но можно удобнее. Будем использовать для конфигурации абстрактный класс AbstractAnnotationConfigDispatcherServletInitializer