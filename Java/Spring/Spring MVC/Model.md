
* Хранит в себе данные
* Взаимодействует с БД для получения данных
* Отдаёт данные котроллеру
## Получение доступа к модели в контроллере:
 
	 @GetMapping("/hello")  
	public String hello(Model model) {  
	    model.addAttribute("message", "Hello World!");  
	  
	    return "first/hello";  
	}