### @Scope

* Говорит о жизненном цикле бина (смотреть [[Bean]])

Примеры:

	@Component  
	@Scope("singleton")  
	public class ClassicalMusic implements Music

	@Component  
	@Scope("prototype")  
	public class ClassicalMusic implements Music