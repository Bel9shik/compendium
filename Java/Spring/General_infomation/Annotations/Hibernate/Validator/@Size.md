	@NotEmpty(message = "Name should mot be empty")  
	@Size(min = 2, max = 30, message = "Name should be between 2 and 30 char")  
	private String name;