### @Qualifier 

Говорит о том какой бин мы хватим использовать

	@Autowired
	@Qualifier ("rockMusic") (требуется указать айди бина)
	private Music music;

Немного необычный синтаксис:

	@Autowired  
	public MusicPlayer(@Qualifier ("classicalMusic") Music classicalMusic, @Qualifier("someRockMusic") Music rockMusic) {  
	    this.classicalMusic = classicalMusic;  
	    this.rockMusic = rockMusic;  
	}

Эквивалентный пример:

	@Autowired  
	@Qualifier ("classicalMusic")  
	private Music classicalMusic;  
	@Autowired  
	@Qualifier("someRockMusic")  
	private Music rockMusic;
