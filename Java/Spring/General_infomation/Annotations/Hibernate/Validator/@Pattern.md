
* позволяет при помощи регулярных выражений проверять строку на шаблон

		// Russia, Moscow, 123456  
		@Pattern(regexp = "[A-Z]\\w+, [A-Z]\\w+, \\d{6}", message = "Your address should be in this format: Country, City, Index")  
		private String address;