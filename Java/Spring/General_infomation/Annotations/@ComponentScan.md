* Аннотация, которая действует также, как и component-scan в .xml файле
* Используется вместе с [[@Configuration]]

Пример:

	@Configuration  
	@ComponentScan("org.NSU.kardash.springCourse.Annotations")  
	public class SpringConfig {  
	}

То же самое:

	<context:component-scan base-package="org.NSU.kardash.springCourse.Annotations"/>