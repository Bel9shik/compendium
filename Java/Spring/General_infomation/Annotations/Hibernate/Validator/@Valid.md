
Говорит о том, что нужно проверять валидность данных

	@PostMapping()  
	public String create(@ModelAttribute("person") @Valid Person person, BindingResult bindingResult) {  
	  
	    if (bindingResult.hasErrors()) {  
	        return "people/new";  
	    }  
	    personDAO.save(person);  
	  
	    return "redirect:/people";  
	}

Важно, что BindingResult **_ДОЛЖЕН_** идти после объекта, валидность которого мы проверяем
