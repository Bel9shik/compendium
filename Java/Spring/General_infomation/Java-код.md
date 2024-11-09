Тут **ВОООБЩЕ** не будет XML. Вся конфигурация через аннотации + Java код

* Для каждого XML тега есть соответствующая аннотация

Смотреть:
[[@Configuration]]
[[@ComponentScan]]
[[@Bean]]
[[@PropertySource]] 

Теперь задание констекта выглядит так:

	public static void main(String[] args) {  
	    AnnotationConfigApplicationContext context = new AnnotationConfigApplicationContext(SpringConfig.class);  
	  
	    MusicPlayer musicPlayer = (MusicPlayer) context.getBean("musicPlayer");  
	  
	    System.out.println(musicPlayer.getVolume());  
	    System.out.println(musicPlayer.getAuthorName());  
	  
	    context.close();  
	}


