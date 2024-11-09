
Говорит как должна вести себя анимация

Пример с использованием [[Image]] и [[ImageView]]:

	Image image = new Image("HBox.png");  
	ImageView imageView = new ImageView(image);  
	pane.getChildren().add(imageView);  
	  
	Line line = new Line(100, 100, 1000, 1000);  
	  
	PathTransition pathTransition = new PathTransition(Duration.seconds(10), line, imageView);  
	pathTransition.setAutoReverse(true);  
	pathTransition.setCycleCount(3);  
	pathTransition.play();

