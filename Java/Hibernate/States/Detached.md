Состояние объекта в Hibernate

![[detached state.png]]

* Объект перестаёт быть Persistent и покидает Persistenct context - становится опыть обычным Java объектом, который Hibernate не отслеживает
* Похоже на Transient состояние
* Это состояние достигается с помощью вызова метода detach() или когда закрывается Hibernate сессия
* Можно присоединить объкт обратно к Persistence context, если вызвать метод merge()
