
#### TOP N записей

### LIMIT

Ключевые слова limit и fetch могут быть использованы для возврата первых n строк или первых n процентов таблицы. Например, запрос:

	select * from employees  
	order by salary desc  
	limit 10;  
  
возвращает первые 10 самых оплачиваемых сотрудников, тогда как запрос:

	select * from employees  
	order by salary desc  
	fetch first 25 percent rows only;  
  
вернет первую четверть записей таблицы.

Другие примеры:

	select distinct * from employees  
	order by salary desc  
	fetch first 5 rows;

--

	select * from employees  
	order by salary desc  
	offset 3 rows  
	fetch next 5 rows only;