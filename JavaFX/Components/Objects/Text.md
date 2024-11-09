Как ни странно текст)))

### Methods:

	* setX(double v) - координаты по Х
	* setY(double v) - координаты по Y
	* setFill(Color color) - установить цвет текста
	* setFont([[Font]] font) 
	* setStyle (String str) - метод для установки стиля CSS. Все использующиеся там проперти нужно знать.
	  Вот пример: text.setStyle("-fx-font-weight: bold; -fx-fill: black; -fx-font-size: 20; -fx-font-style: italic;");
	  Но эта вещь сильнее, чем Font, так как **_КАК МИНИМУМ_** можно сделать градиент, и + это всё описывается в 1 строчку
	  Можно вроде как даже сделать отдельный .css файл и его подключить к text
	* setOnMouseDragged() - повзоляет реагировать на то, что человек двигает текст
	  Пример:
	  text1.setOnMouseDragged((MouseEvent event) -> {  
	    text1.setX(event.getX());  
	    text1.setY(event.getY());  
	});


  ### **_Важно_**

При добавлении листинеров к [[Text]], то нужно вызвать метод text.requestFocus() 
Иначе листинеры работать не будут