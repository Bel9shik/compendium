Объект, который позволяет мапить DTO в объект и объект в DTO

	private Person convertToPerson(@Valid PersonDTO personDTO) {  
	    ModelMapper modelMapper = new ModelMapper();  
	  
	    return modelMapper.map(personDTO, Person.class);  
	}

(нужно подключить зависимость ModelMapper)