Spring сам внедряет все необходимые зависимости в объекты (связывает объекты между собой). Нам необходимо только описать эту связь, Spring сделает всё остальное

![[dependency injection.png]]

#### Способы внедрения зависимостей:

	* Через конструктор
	* Через setter
	* Есть множество конфигураци того, как внедрять (scope, factory method, etc)
	* Можно через XML, аннотации или Java-код
	* Процесс внедрения можно автоматизировать (AutoWiring)

### **Через конструктор**

	public MusicPlayer(Music music) {  
    this.music = music;  
	}

	applicationContext.xml:

	<bean id="musicBean"  
      class="org.NSU.kardash.springCourse.DI.RockMusic">  
	</bean>  
	  
	<bean id = "musicPlayer"  
	      class = "org.NSU.kardash.springCourse.DI.MusicPlayer">  
	    <constructor-arg ref="musicBean"/>  
	</bean>

	В musicPlayer сделали зависмость через конструктор

### **Через Setter**

В MusicPlayer:

	private String authorName;  
	  
	private int volume;  
	  
	public void setAge(int volume) {  
	    this.volume = volume;  
	}  
	  
	public void setAuthorName(String authorName) {  
	    this.authorName = authorName;  
	}


	public void setMusic(Music music) {  
    this.music = music;  
	}


	applicationContext.xml:

	<bean id="musicBean"  
      class="org.NSU.kardash.springCourse.DI.RockMusic">  
	</bean>  
	  
	<bean id = "musicPlayer"  
	      class = "org.NSU.kardash.springCourse.DI.MusicPlayer">  
	      <property name="music" ref="musicBean"/>
	    <property name = "authorName" value="some name"/>
	    <property name = "volume" value="50"/>  
	</bean>

	Из кода выше получился объект MusicPlayer с RockMusic
	authorName = some name
	volume = 50

### **Из внешнего файла**

Удобно:

	* Не нужно каджый раз лезть в applicationContext.xml
	* Хотим все простые значения указать в одном файле


1) 

		musicPlayer.properties:
	
		musicPlayer.authorName=Some name
		musicPlayer.volume=50


2) 
   
	   	<property name = "authorName" value="${musicPlayer.authorName}$"/>
	    <property name = "volume" value="${musicPlayer.volume}"/>  


3) 
   
	   Это добавить в applicationContext.xml:
   
			<context:property-placeholder location="classpath:musicPlayer.properties"/>



Конечный вариант:

	applicationContext.xml

	<context:property-placeholder location="classpath:musicPlayer.properties"/>  
	  
	<bean id="rockMusic"  
	      class="org.NSU.kardash.springCourse.DI.RockMusic">  
	</bean>  
  
	<bean id="classicalMusic"  
	      class="org.NSU.kardash.springCourse.DI.ClassicalMusic">  
	</bean>  
	  
	<bean id="jazzMusic"  
	      class="org.NSU.kardash.springCourse.DI.JazzMusic">  
	</bean>
	<bean id = "musicList"  
      class = "java.util.ArrayList">  
  
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
  
	<bean id="musicPlayer"  
	      class="org.NSU.kardash.springCourse.DI.MusicPlayer">  
	    <property name="authorName" value="${musicPlayer.authorName}"/>  
	    <property name="music" ref="rockMusic"/>  
	    <property name="volume" value="${musicPlayer.volume}"/>  
	    <property name="musicList" ref="musicList"/>  
	</bean>


Тут пример как можно проициалировать сразу список и добавить в плеер через setter




### [[@Autowired]]

Что-то лень самому всё прописывать. На помощь приходит аннотация @Autowired

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


# Внедрение зависимостей в Java - коде:

[[Java-код]]

#### **Было:

	<bean id = "musicPlayer"  
	      class = "org.NSU.kardash.springCourse.DI.MusicPlayer">  
	    <property name="jazzMusic" ref = "musicBean"/>  
	</bean>

#### **Стало:**

	@Configuration  
	public class SpringConfig {  
	    @Bean  
	    public JazzMusic jazzMusic() {  
	        return new JazzMusic();  
	    }  
	    @Bean  
	    public MusicPlayer musicPlayer() {  
	        return new MusicPlayer(jazzMusic());  
	    }  
	}