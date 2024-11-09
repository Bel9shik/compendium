#### Оператор CREATE TABLE

Для создания новой таблицы необходимо использовать оператор CREATE TABLE, синтаксис которого имеет вид:

	CREATE TABLE table
	
	( column1 type1 [(size1)][CONSTRAINT _
	column-constraint1]
	
	[, column2 type2 [(size2)][CONSTRAINT _
	
	column-constraint2]
	
	[, ...]]
	
	[CONSTRAINT table-constraint1 _
	
	[,table-constraint2 [, ...]]]);

В этом операторе следует указать имя поля, тип данных для него (тип данных должен поддерживаться данной СУБД), длину (для некоторых типов полей) и, если нужно, серверные ограничения (с применением ключевого слова CONSTRAINT). Например, следующий запрос создает таблицу с именем Simple с четырьмя колонками — LastName, FirstName, EMail и HomePage:

Примеры:

	CREATE TABLE projx
	(
	
	projno int4 NOT NULL
	
	, pname bit varying (14) CHECK (SUBSTR(pname,1,1) BETWEEN 'A' AND 'Z')
	
	, bdate DATE DEFAULT TRUNC ( SYSDATE )
	
	, budget numeric(10,2) CHECK (budget > 0)
	
	, str text
	
	, CONSTRAINT C1 CHECK (str like 'A*')
	
	);

  

	CREATE TABLE lessons (
	
	subjectname VARCHAR(30),
	
	teachertnp NUMBER(2) references teachers(tnp),
	
	foreign key (subjectname) references subjects(subjectname),
	
	);

