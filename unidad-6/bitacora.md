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

- **Identifica los Roles:**

  - ¿Qué clase actúa como la interfaz Observer? ¿Qué método define?
 
    - La clase que funciona como observer en este caso sería Particle, puesto que es la única que hereda de esta. El método que sobreescribe es el de notify(). 

  - ¿Qué clase actúa como Subject? ¿Qué métodos proporciona para gestionar observadores y notificar?

    - La clase que actua como subject sería ofApp, y los métodos utilizados para interactuar con los observers serían los siguientes:
    - <img width="339" height="281" alt="image" src="https://github.com/user-attachments/assets/0fba5b77-7fa6-4340-afb7-a56e4c684a40" />

  - ¿Qué clase es el ConcreteSubject en esta aplicación? ¿Por qué? (Pista: ¿Quién envía las notificaciones?)

    -  Las notificaciones las envia ofApp, entonces creooooooo que esa sería el concreteSubject.

  - ¿Qué clase(s) actúan como ConcreteObserver? ¿Por qué? (Pista: ¿Quién recibe y reacciona a las notificaciones?)

    - Diría que son todas las particulas que heredan de observer, puesto que a ellas les llega información del cambio en subject y a partir de eso cambian su estado.  

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

   - <img width="967" height="340" alt="image" src="https://github.com/user-attachments/assets/0a3c00c7-b22d-4e2d-80e7-a7ccbb4ae72d" />

   - Con este diagrama es fácil identificar la relación que existe entre los observadores y los sujetos, se ve como ofApp lleva un registro de todas las particulas y los métodos que puede controlar su estado y que información les pasa. Adicionalmente tambien es curiosa la relación de herencia que tiene Particle y ofApp, pues ambos heredan de clases abstractas, por lo que la única forma de estas clases de tener una instancia sería por medio de Particle y ofApp.

 
 - **3.) Construye un diagrama de secuencia que muestre cómo funciona el patrón Observer al presionar una tecla.**

   -   <img width="846" height="458" alt="image" src="https://github.com/user-attachments/assets/8da41bf3-373a-460a-8b8e-c59c916cf817" />

   -   En este diagrama se observa claramente el patrón observer, desde que cambia el estado del subject hasta que notifica cada una de las particulas, mostrando su caracteristica principal que es esa relación de uno a muchos.
 
 - **4.) ¿Qué ventajas crees que ofrece usar el patrón Observer en esta aplicación en comparación con, por ejemplo, que ofApp::update recorriera todas las partículas y les dijera directamente que cambien su comportamiento basado en una variable global?**

   - Pienso que el flujo de instrucciones de la aplicación es mucho más claro y organizado, sin embargo me parece que es menos eficiente, lo digo más que todo por que un estado en este caso es una clase y encima todos los llamados que debe hacer a otros métodos (como vimos en la unidad pasada) son bastante demandantes, sin embargo si me parece que es un metodo que escala mucho más fácil, en el sentido en el que se controla las partes del código que deben estar atentas a lo que sucede y añadir o quitar reacciones no cuesta para nada puesto que solo están definidas una vez.
  
## Actividad 3

- **Identifica la Factory:**

  - ¿Qué clase actúa como la factory en este ejemplo?
  
    - En este ejemplo sería la clase ParticleFactory, la cual solo tiene un método estático que devuelve Particle* y se llama createParticle(const std::string & type)
      
  - ¿Cuál es el “método factory” específico? ¿Es un método de instancia o estático?

    - No había visto esta pregunta, pero es un método estático que recibe una string. 

  - ¿Qué tipo de objeto devuelve este método fábrica?

    - Devuelve un puntero que apunta a un objeto de tipo Particula. 

- **Proceso de creación:**

  - Observa el método ParticleFactory::createParticle. ¿Cómo decide qué tipo de partícula específica crear y configurar?

    - Utiliza la string que recibe como parámetro para decidir los valores de los atributos de cada particula como color, tamaño y velocidad. No sin antes crear una particula al principio del método.

  - ¿Qué información necesita el método fábrica para realizar su trabajo?

    - Diría que necesita dos cosas fundamentales, la string que le pasan de parámetro y la particula que crea dentro del método. 

  - ¿Qué devuelve si se le pasa un tipo desconocido? ¿Cómo podrías mejorar esto?

    - Si se le pasa un tipo desconocido igual devuelve una particula, el tema es que esta particula va a tener null los atributos de color, tamaño y velocidad.
    - Para arreglar esto se me ocurre añadir un else que inicialice estos valores. 

- **Uso de Factory:**

  - Localiza ofApp::setup. ¿Cómo se utiliza la ParticleFactory para poblar el vector particles?

    - Lo que hace es que corre 3 for loop donde llama ParticleFactory::createParticle() pasando como parametro en cada uno de los for un tipo diferente de particula. adicionalmente las subscribe como observers del subject. 

  - Compara esto con la alternativa: ¿Cómo se vería ofApp::setup si no usara la fábrica y tuviera que crear y configurar cada tipo de partícula (star, shooting_star, planet) directamente usando new Particle() y luego ajustando sus propiedades (size, color, velocity)?

    - Tendría que hacer el mismo for, pero tendría que llenar la información del constructor de particula, lo tendría que hacer 3 veces y no sería tan simple como la opción que tenemos acá. es decir, sería más extenso de escribir.

___

- **1.) Explica con tus propias palabras el propósito del patrón Factory Method (o Simple Factory, en este caso). ¿Qué problema principal aborda en la creación de objetos?**

  - Soluciona varios problemas, en un principio facilita la creación de nuevos objetos, lo otro es que desde la interfaz no se necesita saber como crear una particula, por lo que este proceso elimina la necesidad de tener este conocimiento. En si tener esta opción facilita la creación de particulas nuevas.

- **2.) ¿Qué ventajas aporta el uso de ParticleFactory en ofApp::setup en comparación con instanciar y configurar las partículas directamente allí? Piensa en términos de organización del código (SRP - Single Responsibility Principle), legibilidad y facilidad para añadir nuevos tipos de partículas en el futuro.**

  - Pues le delega la creación de particulas a un método especifico y ahora desde setup() no tenemos que añadir la lógica de instanciación de una particula, por otro lado es un poquito cierto que si es mucho más legible, si y solo si se sabe del proposito de particleFactory(), otra cosa que si me gusta bastante de esta forma de crear objetos es que añadir un tipo nuevo de particula es mucho más fácil, bueno, la integración puede ser mucho más extensa pero es más legible. 

- **3.) Imagina que quieres añadir un nuevo tipo de partícula llamada "black_hole" que tiene tamaño grande, color negro y velocidad muy lenta. Describe los pasos que necesitarías seguir para implementar esto utilizando la ParticleFactory existente. ¿Tendrías que modificar ofApp::setup? ¿Por qué sí o por qué no?**

  - En un principio hay que modificar ParticleFactory::createParticle() donde habrá que añadir un else if que sea if(type=="black_hole") y dentro de este hay que particle->size = ofRandom(10.0f, 12.0f); particle->color = ofColor(20, 20, 20); Ya depues de hacer esto lo único que habría que hacer sería añadir otro for en setup() y dentro de ese for hacer el llamado a  ParticleFactory::createParticle() y subscribirlas al Subject.

- **4.) El método createParticle en el ejemplo es estático. ¿Qué implicaciones (ventajas/desventajas) tiene esto comparado con tener una instancia de ParticleFactory y un método de instancia createParticle()?.**

  - Pues en un principio que no toca instanciar la clase que lo contiene para poder hacer llamados, cosa que sería totalmente innecesaria, puesto que es una clase completamente de comportamiento y no requiere tener una instancia, adicionalmente, por poquito que sea tambien es una decisión que nos ahorra memoria.  

## Actividad 4

- **Identifica los componentes:**

  - ¿Cuál es la clase Context? ¿Qué miembro utiliza para mantener el estado actual?

    - Creo que la clase Context sería Particle::setState(State * newState), que mantiene una instancia de state y mantiene su estado actual. 

  - ¿Cuál es la interfaz State? ¿Qué métodos importantes define? (Piensa en update, onEnter, onExit).

    - define 3 métodos, update(), onEnter() y onExit() 

  - Enumera las clases ConcreteState. ¿Qué comportamiento específico encapsula cada una?

    - Las clases ConcreteState serían: NormalState, ReppelState, StopState, AttractState y el comportamient que cada una encapsula sería el método update(). 

- **Delegación del comportamiento:**

  - Observa el método Particle::update(). ¿Cómo delega la lógica de actualización al estado actual?

    - chequea si hay un state definido (state es un atributo local de Particle) y llama el método update() de ese estado. 

  - Compara el código dentro de NormalState::update(), AttractState::update(), RepelState::update() y StopState::update(). ¿Cómo encapsula cada clase un comportamiento diferente?

    - Cada una se encarga de sobreescribir el método update entonces de esa forma, cada que se llama el método update de estos estados cada uno es diferente. 

- **Transiciones de estado:**

  - ¿Cómo cambia una Particle de un estado a otro? ¿Qué método es responsable de gestionar la transición? (Busca setState).

    - basicamente recibe un nuevo estado y cambia el puntero state a ese nuevo que recibió.

  - ¿Qué sucede dentro de Particle::setState()? ¿Por qué son importantes los métodos onEnter y onExit de la interfaz State (aunque no todos los estados concretos los usen extensivamente en este ejemplo)? ¿Qué gestionan onEnter y onExit en NormalState?

    - me imagino que onEnter será para inicializar un par de variables que se usaran constantemente. OnExit diría que es para limpiar oh resetear las variables que se van a usar.

  - ¿Qué evento externo (mediado por el patrón Observer, que ya analizaste) desencadena la llamada a setState en una Particle?

    - onNotify(), es el que se encarga de llamar este metodo en cada particula y cambiar el estado.


  
