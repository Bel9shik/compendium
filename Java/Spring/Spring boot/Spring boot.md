Проблема Spring Framework проблема в том, что много конфигурации. Spring boot решает эту проблему!

Spring boot - ещё одна часть Spring Framework (также, как [[Spring MVC]], Spring Core, [[Spring Security]] ), который упрощает конфигурацию и разработку. Все остальные компоненты Spring Framework остаются.

* Spring Boot предугадывает самую логичную конфигурацию, поэтому нам в большинстве случаев не надо ничего конфигурировать (конфигурация по умолчанию делает то, что надо). Например, мы подключили в pom.xml зависимость Thymeleaf. Spring Boot увидит эту зависимость и Thymeleaf автоматически заработает (конфигурация не нужна!).

* Spring Boot предоставляет внутренний Web сервер. 

* Spring Boot Starters.  Решает проблему зависимостей и их совместимостей. Зависимости сгруппированы в так называемые стартеры --> подключаем их, а не все зависимости, тогда проблем с совместимостью не будет. Например Spring Boot Starter Web содержит в себе spring-core, spring-web, spring-webmvc, ...

		@SpringBootApplication  
	public class SpringCourseApplication {  
	  
	    public static void main(String[] args) {  
	       SpringApplication.run(SpringCourseApplication.class, args);  
	    }  
	  
	}

Для удобного создания можно использовать Spring Initilizr (https://start.spring.io/), после чего зайти в папку через IntelliJ IDEA.

### Недостатки:
* Из-за большего количества "магии" под капотом, то могут появляться сложно устранимые ошибки