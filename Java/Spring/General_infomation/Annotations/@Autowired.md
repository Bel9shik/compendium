### @Autowired 

Позволяет внедрять зависимости автоматически

* Мы больше не внедряем зависимость вручную, Spring сам ищет подходящий бин и автоматически внедряет его

#### **Было**: 


	<bean id="musicBean"  
      class="org.NSU.kardash.springCourse.DI.RockMusic">  
	</bean>  
	  
	<bean id = "musicPlayer"  
	      class = "org.NSU.kardash.springCourse.DI.MusicPlayer">  
	    <constructor-arg ref="musicBean"/>  
	</bean>


#### **Стало**:

	@Autowired  
	public MusicPlayer(Music music) {  
	    this.music = music;  
	}



* Если находится один подходящий бин, то он внедряется в качестве зависимости
* Если не находится ни одного бина - ошибка
* Если несколько бинов подходят - неоднозначность


#### **Можно использовать на (даже на приватных полях):
1) Конструкторах
2) Полях
3) Сеттерах