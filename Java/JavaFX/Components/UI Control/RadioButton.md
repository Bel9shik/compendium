Разновидность кнопки

	RadioButton r1 = new RadioButton("Yes");  
	RadioButton r2 = new RadioButton("No");  
	RadioButton r3 = new RadioButton("Don't know");  
	  
	r1.setLayoutX(500);  
	r1.setLayoutY(500);  
	r2.setLayoutX(500);  
	r2.setLayoutY(520);  
	r2.setLayoutY(520);  
	r3.setLayoutX(500);  
	r3.setLayoutY(540);
	
	pane.getChildren().addAll(r1, r2, r3);


Можно сделать так, чтобы можно было выбрать только 1 вариант (через [[ToggleGroup]])

