
### @Value

* Говорит, что нужно инициализировать это значение из файла


		1)	musicPlayer.properties:
		
		musicPlayer.authorName=Some name
		musicPlayer.volume=50

		2) applicationContext.xml:
		   
		   <context:property-placeholder location="classpath:musicPlayer.properties"/> 
	
		3) @Value("${musicPlayer.authorName}")  
			private String authorName;  
			@Value("${musicPlayer.volume}")  
			private int volume;

