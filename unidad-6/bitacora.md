# Bitácora de aprendizaje de la unidad 6

## Actividad 1

- **1.) ¿Cómo puedes interactuar con la aplicación?**

  - Se puede interactuar por medio de cuatro inputs, s, a, r y n. En ese orden, el comportamiento de cada una sobre las particulas es: Stop congela la posición de las particulas hasta que se presione de nuevo, Attract interpola la posición de las particulas al del mouse, Reppel aleja las particulas del mouse y Normal que se encarga de que su comportamiento sea normal.

- **2.) ¿Observas los diferentes tipos de “partículas”? ¿Se comportan todas igual inicialmente?**

  - A simple vista parece que todas se comportan de igual forma, lo que sucede es que su velocidad color y tamaño es diferente, pero esto solo desde el estado inicial es a única diferencia notable. En total cuento 3, una bolita verde que es muy rápida y pequeña, otra que es grande y azul y por último una verde, tengo la sospecha de que estas dos últimas tienen la misma velocidad.
 
- **3.) Toma algunas capturas de pantalla de la aplicación en diferentes momentos**

**INICIAL**
<img width="1014" height="751" alt="image" src="https://github.com/user-attachments/assets/61ae4c93-0681-4cd1-82dd-be0985f83add" />

**ATRACT**
<img width="1015" height="762" alt="image" src="https://github.com/user-attachments/assets/d2e7fce0-c84a-4dbd-a4f3-f1ac249d79ff" />

**REPPEL**
<img width="1019" height="768" alt="image" src="https://github.com/user-attachments/assets/8c780e52-2bd5-4118-b6e5-aedd84f2d817" />

**STOP** (están quietas)
<img width="1018" height="764" alt="image" src="https://github.com/user-attachments/assets/69fc179a-28e3-4453-b18f-7949c179787e" />

**NORMAL**
<img width="1018" height="768" alt="image" src="https://github.com/user-attachments/assets/716c9e35-f7fa-4861-b5bf-6d17a85f262b" />

- **4.) ¿Qué crees que está pasando “detrás de cámaras” cuando presionas las teclas?**

  - Pues el profe en este momento me está explicando justo lo que pasa detrás de camaras, pero me voy a hacer el bobo y voy a decir lo que diría si no supiera. Diría que cada frame se está actualizando la posición de cada particula con respecto a una variable que corresponde al input, y esta es la que define el como cambia en el tiempo la velocidad y posición de las particulas.

## Actividad 2
___

- **Identifica los Roles:**

  - ¿Qué clase actúa como la interfaz Observer? ¿Qué método define?
 
    - La clase que funciona como observer en este caso sería Particle, puesto que es la única que hereda de esta. El método que sobreescribe es el de notify(). 

  - ¿Qué clase actúa como Subject? ¿Qué métodos proporciona para gestionar observadores y notificar?

    - La clase que actua como subject sería ofApp, y los métodos utilizados para interactuar con los observers serían los siguientes:
    - <img width="339" height="281" alt="image" src="https://github.com/user-attachments/assets/0fba5b77-7fa6-4340-afb7-a56e4c684a40" />

  - ¿Qué clase es el ConcreteSubject en esta aplicación? ¿Por qué? (Pista: ¿Quién envía las notificaciones?)

    -  

  - ¿Qué clase(s) actúan como ConcreteObserver? ¿Por qué? (Pista: ¿Quién recibe y reacciona a las notificaciones?) 
- **Sigue el flujo de notificación:**
  - Localiza el método keyPressed en ofApp.cpp. ¿Qué sucede cuando se presiona la tecla ‘a’? ¿Qué método se llama?
  - Ve al método notify en la clase Subject. ¿Qué hace este método?
  - Localiza el método que implementa la interfaz Observer en la clase Particle (onNotify). ¿Qué hace este método cuando recibe el evento “attract”? 
- **Registro y eliminación de observadores:**
  - ¿En qué parte del código se añaden las instancias de Particle como observadores de ofApp? (Busca dónde se llama a addObserver).
  - ¿Dónde se eliminarían los observadores si fuera necesario (por ejemplo, si una partícula se destruyera durante la ejecución)? (Busca removeObserver). ¿Por qué es importante el destructor de ofApp en este contexto? 
___

- **1.) Explica con tus propias palabras el propósito del patrón Observer. ¿Qué problema resuelve?**

  -  El patrón observer resuelve la relación entre un objeto al que le interesa un cambio en el otro, normalmente esto se implementaría de tal forma en la que independientemente el objeto está pendiente de los atributos que le importan de otro, el problema con esta implementación es que no escala muy bien, si tengo un caso donde muchos objetos tengan que estar prestando atención a lo que sucede en otro es más organizado (aunque menos eficiente computacionalmente) utilizar observadores los cuales resuelven este problema, puesto que se suscriben a un "evento" y de esa forma están atentos a cuando sucede un cambio.
 
 - **2.) Dibuja un diagrama que muestre la relación entre Subject, Observer, ofApp y Particle en el caso de estudio, indicando quién es el Sujeto y quiénes los Observadores.**

   - 
 
 - **3.) Construye un diagrama de secuencia que muestre cómo funciona el patrón Observer al presionar una tecla.**

   -   
 
 - **4.) ¿Qué ventajas crees que ofrece usar el patrón Observer en esta aplicación en comparación con, por ejemplo, que ofApp::update recorriera todas las partículas y les dijera directamente que cambien su comportamiento basado en una variable global?**

   - 
