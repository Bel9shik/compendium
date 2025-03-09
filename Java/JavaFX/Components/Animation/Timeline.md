Более гибкая, чем [[FadeTransition]] и [[PathTransition]]. В прицнипе он один из обоих может заменить

Пример:

	Timeline timeline = new Timeline(new KeyFrame(Duration.millis(500), new EventHandler<ActionEvent>() {  
	  
	    boolean b = true;  
	  
	    @Override  
	    public void handle(ActionEvent actionEvent) {  
	        if (b) {  
	            button.setLayoutX(100);  
	            button.setLayoutY(300);  
	            b = false;  
	        } else  {  
	            button.setLayoutX(150);  
	            button.setLayoutY(350);  
	            b = true;  
	        }  
	    }  
	}));  
	  
	timeline.setCycleCount(Timeline.INDEFINITE); 
	timeline.play();