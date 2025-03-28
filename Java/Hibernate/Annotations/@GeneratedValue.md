Аннотация показывает, что текущая таблица автоматически генерируется базой данных

	@Id  
	@Column(name = "id")  
	@GeneratedValue(strategy = GenerationType.IDENTITY)  
	private int id;

Обязательно указать стратегию. Всего возможно 4 варианта:
* IDENTITY
* AUTO
* SEQUENCE
* UUID
* TABLE