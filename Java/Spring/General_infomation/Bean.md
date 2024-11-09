 * Это просто Java объект
* Когда Java объекты создаются с помощью Spring'a, они называются бинами (beans)
* Бины создаются из Java классов (так же, как и обычные объекты)

	Пример создания бина через конфигурационный файл:

		<bean id="testBean"  
			class="org.NSU.kardash.springCourse.TestBean">  
			<constructor-arg value="Neil"/>  
		</bean>


Используется паттерн Singleton. При создании объекта в контексте хранится 1 объект и каждый раз, когда дерём объект из контекста - это один и тот же объект (это используется по умолчанию)

### Scopes

##### Singleton

По умолчанию используется паттерн Singleton. При создании объекта в контексте хранится 1 объект и каждый раз, когда дерём объект из контекста - это один и тот же объект 


##### Prototype

Scope, который каждый раз создат новый объект при вызове getBean()

![[prototype.png]]

	Пример:

	<bean id = "musicList"  
	      class = "java.util.ArrayList"  
	        scope="prototype">  
	  
	        <constructor-arg>  
	            <list>  
	                <ref bean="rockMusic"/>  
	                <ref bean="rockMusic"/>  
	                <ref bean="rockMusic"/>  
	                <ref bean="jazzMusic"/>  
	                <ref bean="classicalMusic"/>  
	            </list>  
	        </constructor-arg>  
	  
	</bean>


#### Для этих бинов Spring не вызывает destroy-method

Spring не берёт на себя полный жизненный цикл бинов со scope "prototype". Spring отдаёт prototype бины криенту и больше о них не заботится (в отличии от singleton бинов)


### Жизненный цикл бина (bean lifecycle)

![[bean lifecycle.png]]

#### init-method

	* Метод, который запускается в ходе инициализации бина
	* Инициализация ресурсов, обращение к внешним файлам, запуска БД


#### destroy-method

	* Метод, который запускается в ходе уничтожения бина (при завершении приложения)
	* Очищение ресурсов, закрытие потоков ввода-вываода, закрытие доступа к БД


Как это выглядит к коде:

	<bean id="classicalMusic"  
	      class="org.NSU.kardash.springCourse.DI.ClassicalMusic"  
		init-method="doMyInit"  
		destroy-method="doMyDestroy">  
	</bean>


#### Тонкости init и destroy методов

	1) Модификатор доступа
		У этих методов может быть любой модификатор доступа (public, protected, private)
	2) Тим возвращаемого значения
		Может быть любой, но чаще всего void (тк нет возможности получить возвращаемое значение)
	3) Название метода
		Название может быть любым
	4) Аргументы метода
		Эти методы !не должны! принимать на вход какие-либо аргументы


### Factory-method

	Вкратце: паттерн "фабричный метод" предлагает создавать объекты не напрямую, используя оператор new, а через вызов особого фабричного метода. Объекты всё равно будут создаваться при помощи new, но делать это будет фабричный метод (иногда это бывает удобно)

	<bean id="classicalMusic"  
      class="org.NSU.kardash.springCourse.DI.ClassicalMusic"  
      init-method="doMyInit"  
      destroy-method="doMyDestroy"  
	scope="prototype"  
	factory-method="getClassicalMusic">  
	</bean>

Стоит отметить, что фэктори-метод должен быть static

	public static ClassicalMusic getClassicalMusic() {  
    return new ClassicalMusic();  
}


Нужно понимать какой scope использовать
Если будет singleton, то Spring один раз вызовет factory-method и больше не будет. Если же scope = prototype, то при каждом вызове будет вызываться factory-method