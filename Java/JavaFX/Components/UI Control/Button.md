Создаёт кнопку

	Button button = new Button("Click me");  
	button.setStyle(cssStyle);
	button.setOnAction(new ButtonListener());

setOnAction() используется для того, чтобы реагировать на действия пользователя

	class ButtonListener implements EventHandler<ActionEvent> {  
  
	    @Override  
	    public void handle(ActionEvent actionEvent) {  
	        if (circle.getRadius() == 0) circle.setRadius(100);  
	        else circle.setRadius(circle.getRadius() - 10);  
	    }  
	}

Внутри ButtonListener и происходит обработка нажатия на кнопку