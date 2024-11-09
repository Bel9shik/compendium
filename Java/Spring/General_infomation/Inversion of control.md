![[inversion of control.png]]


#### Проблема #3: MusicPlayer сам создаёт свои зависмости. Это архитектурно неправильно - противоречит принципу IoC.

	Решение: использовать принцип IoC


Как из видно из картинки, что:

	* MusicPlayer зависит от ClassicalMusic
	* MusicPlayer сам создаёт объект ClassicalMusic
	* Вместо этого мы хотим передавать объект ClassicalMusic внутрь MusicPlayer - это и называется инверсией управления (IoC)

#### Решение:

	class MusicPlayer {
		private Music music;
				public MusicPlayer (Music music) {
					this.music = music;
				}
		public void playMusic() {
			// Тут больше не создаём объекты
			// ... Код для воспроизведения музыки
		}
	}

![[invercion of control last problem.png]]

	applicationContext.xml:

	<!--    <bean id="musicBean"-->  
	<!--          class="org.NSU.kardash.springCourse.IoC.RockMusic">-->  
	<!--    </bean>-->