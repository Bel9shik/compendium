* Помечает класс
* Часто работает вместе с [[@Table]] и [[@Column]]

Нужна для того, чтобы сказать Hibernate, что в базе данных существует такая сущность: 

	@Entity  
	@Table(name = "Person" )  
	public class Person {  
	      
	    @Id  
	    @Column(name = "id")  
	    private int id;  
	  
	    @Column(name = "name")  
	    private String name;  
	  
	    @Column(name = "age")  
	    private int age;  
	  
	    public void setId(int id) {  
	        this.id = id;  
	    }  
	  
	    public int getId() {  
	        return id;  
	    }  
	}