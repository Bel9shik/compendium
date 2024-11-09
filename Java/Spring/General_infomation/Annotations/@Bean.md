* Используется в конфигурации для задания бинов
* Название метода = айди бина
* По умолчанию стоит scope = singleton, это значит что тело @Bean методов по умолчанию вызывается только один раз, а все последующие вызовы Spring прерывает и возвращет уже имеющийся бин из контекста

Пример:

	<bean id="jazzMusic"  
	      class="org.NSU.kardash.springCourse.DI.JazzMusic">  
	</bean>

равен:


	@Configuration  
	public class SpringConfig {  
	    @Bean  
	    public JazzMusic jazzMusic() {  
	        return new JazzMusic();  
	    }  
	}


В примере выше айди бина = "jazzMusic"


