Аннотация, которая указывает на какой именно столбец нужно смотреть при заполнении данными объект

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