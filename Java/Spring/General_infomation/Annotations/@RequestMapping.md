
Говорит о дефолтном пути до файла

Пример:

	@Controller  
	@RequestMapping("/first")  
	public class FirstController {  
	  
	    @GetMapping("/hello")  
	    public String hello() {  
	        return "first/hello";  
	    }  
	  
	    @GetMapping("/goodbye")  
	    public String goodBye() {  
	        return "first/goodbye";  
	    }  
	  
	}


В этом случае эти методы будут активны при переходе по ссылке .../first/hello и .../first/goodbye

