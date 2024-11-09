* От англ. "получить"
* Самый используемый запрос (переход по ссылке, поисковый запрос в Google, открытие видео на YouTube и тд)
* Идемпотентный (ничего не меняет на сервере)
* Тело запроса пустое

Тело пустое, но что делать, если нужно как-то отправить дополнительные параметры?

* Параметры помещаются в самом URL после знака "?" в формате **_ключ=значение_** 
* Несколько параметров (пар **_ключ=значение_**) разделяются знаком &

### Обработка параметров

* Через получение ВСЕГО запроса (HttpServletRequest)
* Через аннотацию [[@RequestParam]]

Второй вариант предпочтительнее, так код становится более читабельным + при первом варианте мы получаем ВСЮ информацию о запросе, и если нам нужны только параметры, то это не столь безопасно получается. 

**_НО_** во втором способе при отсутствии параметров будет возвращён 400ый код ошибки. Чтобы такого не было нужно добавить дополнительно "required = false":

Итог: 
* первый вариант, если нужно много инфы о запросе
* второй вариант, если нужны ТОЛЬКО параметры

Примеры:

Через HttpServletRequest:

	@GetMapping("/hello")  
	public String hello(HttpServletRequest request) {  
	  
	    String name = request.getParameter("name");  
	  
	    System.out.println("Hello, " + name);  
	  
	    return "first/hello";  
	}

Через [[@RequestParam]]:

	@GetMapping("/hello")  
	public String hello(@RequestParam("name") String name) {  
	  
	    System.out.println("Hello, " + name);  
	  
	    return "first/hello";  
	}

	С required = false:

	@GetMapping("/hello")  
	public String hello(@RequestParam(value = "name", required = false) String name) {  
	  
	    System.out.println("Hello, " + name);  
	  
	    return "first/hello";  
	}
