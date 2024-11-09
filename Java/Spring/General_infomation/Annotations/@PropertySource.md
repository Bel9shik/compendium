* Используется вместе с [[@Configuration]] 
* Нужен для указания пути для .properties файла
* Используется для внедрения зависимостей в Spring

#### **Теперь:**

1) .properties файл:
   
		musicPlayer.authorName = Some Name
		musicPlayer.volume = 60
   
2) SpringConfig.java:
   
		@Configuration  
		@PropertySource("classpath:musicPlayer.properties")  
		public class SpringConfig {  
		}   

3) MusicPlayer.java:

		@Value("${musicPlayer.authorName}")  
		private String authorName;  
		  
		@Value("${musicPlayer.volume}")  
		private int volume;