
Плавно убирает прозрачность (через некоторое время все элементы станут с той прозрачностью, что будет указано). В примере снизу все элементы становятся невидимыми:

	FadeTransition fadeTransition = new FadeTransition(Duration.seconds(5), pane);  
	fadeTransition.setFromValue(1.0);  
	fadeTransition.setToValue(0.0);  
	fadeTransition.setCycleCount(3);  
	fadeTransition.setAutoReverse(true);  
	fadeTransition.play();

Можно работать прям с [[Pane]]. Не обязательно только с картинками!!!!