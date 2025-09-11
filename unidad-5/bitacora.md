# Bitácora de aprendizaje de la unidad 5

## 1. 🐸 **Diagnóstico inicial** 🐸

___

### 🪸 **Parte 1: recordando los conceptos (en C#)** 🪸

1.) ¿Qué es el encapsulamiento para ti?

- Como evitar el acceso a metodos o atributos por medio de public, private, protected y el otro que no me acuerdo. Esto sirve para que algunos atributos o métodos solo puedan ser accedidos por la clase que los contiene.

2.) ¿Qué es la herencia?

- La herencia es utilizada para el polimorfismo, esta permite que una clase tenga subclases que **heredan** sus atributos y métodos, de esta forma es mucho más facil implementar clases derivadas.

3.) ¿Qué es el polimorfismo?

- Creo que el polimorfismo hace referencia a la reutilización de métodos, es decir, darle diferentes usos a un solo metodo utilizando abstract y override para sobreescribir el método y darle diferentes comportamientos.

### 🪸 **Parte 2: análisis de código (en C#)** 🪸

1.) Señala una línea de código que sea un ejemplo claro de encapsulamiento

**Encapsulamiento**

> private string nombre;

- Es un ejemplo de encapsulamiento puesto que utiliza la palabra reservada private, y de esta forma solo puede ser accesible por la clase que la contiene, es por eso que tiene un método accesor (?) este permite realizar un chequeo de la variable y así evitar que se le de un valor inadecuado.

2.) ¿Por qué crees que el campo nombre es private pero la propiedad Nombre es public? ¿Qué problema se evita con esto?

- No sabía que esta era la siguiente pregunta. Pero basicamente ese método que está en public normalmente se utilizar para proteger el atributo "real" que es el que está privado, es un metodo que puede leer y cambiar ese atributo privado pero además puede  definir unas reglas por las cuales decide si le cambia o no el valor a ese atributo, de esa forma evita que el atributo privado cambie su valor a algo inadecuado.

**Herencia**

1.) ¿Cómo se evidencia la herencia en la clase Circulo?
  
  - Se evidencia en dos instancias; La primera siendo su constructor, donde hereda el nombre de figura y ya viene definido como "Círculo". La otra sería cuando implementa el método Dibujar(), este lo hereda de *Figura* sin embargo se le indica que lo debe sobreescribir y añadir un comportamiento propio de el.

2.) Un objeto de tipo Circulo, además de Radio, ¿Qué otros datos almacena en su interior gracias a la herencia?

- El método del que hablé y el nombre.

**Polimorfismo**

1.) Observa el bucle foreach.  ¿Cómo crees que funciona esto “por debajo”?

No tengo la menor idea. Pero me imagino que por medio de los punteros que componen la lista este foreach pasa por cada uno ejecutando el método indicado, pero realmente hasta ahí me llega la imaginación. Se que esto se hace en el heap puesto que la lista y los objetos que tiene son variables dinámicas pero más allá de eso pienso que si es recorriendo la lista, chequeando que el objeto en el que va si es una figura y por último ejecutando el método correspondiente.

### 🪸 **Parte 3: hipótesis sobre la implementación** 🪸 

1.) Cuando creas un objeto Rectangulo, este tiene Base, Altura y también Nombre. ¿Cómo te imaginas que se organizan esos tres datos en la memoria del computador para formar un solo objeto?

- Me imagino que cuando se crea se refiere a instanciar el objeto, por lo que creo que esa instancia de Rectangulo crea copias de esos 3 atributos a los cuales, como objeto, está apuntando, y esos punteros son los que junto al objeto se guardan en el Heap. Sin embargo, creo que para el caso del Nombre es diferente puesto que este tiene que primero crear una copia del atributo de quien hereda, más no de el mismo. Realmente no tengo ni idea pero si pienso que un objeto está guardado en el heap y está compuesto por copias de atributos de la clase a la que pertenece.

2.) Pensemos de nuevo en la llamada fig.Dibujar(). El compilador solo sabe que fig es una Figura. ¿Cómo decide el programa, mientras se está ejecutando, si debe llamar al Dibujar del Circulo o al del Rectangulo?

- Creo que es como lo dije más temprano, el foreach recorre la lista por medio de los punteros, entonces cuando llega a un objeto que es una Figura este no lo observa como algo tan general puesto que tiene acceso al objeto específico por medio de los punteros, de esta forma, ese momento *fig* es realmente ese objeto. De esa forma el programa sabe que método llamar.

3.) ¿Cómo crees que el compilador logra que no puedas acceder a un miembro private desde fuera de la clase? ¿Es algo que se revisa cuando escribes el código, o es una protección que existe mientras el programa se ejecuta?

- No tengo ni idea. Diría que tambien es por medio de punteros, y me refiero a que si se intenta acceder a ese atributo por medio de un puntero que no sale de la clase entonces este no podrá ser accedido, y diría que el filtro se hace por medio de los objetos, que permiten acceder a esos punteros. Y pienso eso por que es lo único que se me ocurre, definitivamente es algo con los punteros, pero como realmente funcione no sé.

### 🪸 **Parte 4: y tu autoevaluación y primeras preguntas** 🪸

- Voy a definir una pregunta pero igual me voy a ir por la ruta guiada esperando que eventualmente me respondan a mi pregunta.

1.) ¿Como funciona la manipulación de la memoria en C++ cuando se implementan los conceptos de herencia, encapsulamiento y polimorfismo?

___

## 2. 🐸 **La pregunta inicial** 🐸

- ***¿Como funciona la manipulación de la memoria en C++ cuando se implementan los conceptos de herencia, encapsulamiento y polimorfismo?***

## 3.  **Registro de exploración:** 

> Aquí documentas cada ciclo de pregunta -> hipótesis -> experimento -> hallazgo -> reflexión.
> Debe ser rico en evidencia visual (código, capturas del depurador con anotaciones, diagramas).

### Actividad 02

- **Analiza el código de la aplicación y trata de explicar en tus propias palabras qué está haciendo**

El código cada frame está chequeando por 3 inputs, click izquierdo, espacio y la s, el más interesante de estos tres es el click izquierdo puesto que este llama el método createRisingParticle() el cual se encarga de "calcular" todos los parámetros necesitados para crear una particula de este tipo y de esa forma, al final del método, llamar el método constructor de la particula para pasarle esos parámetros.

Este tipo de particula hereda gran parte de sus carácteristicas de una clase base llamada Particula, la cual solamente declara varios métodos en virtual para que sean o no sobreescritos, de estos los más interesantes son los métodos de update() y draw(). El primero se encarga de modificar la edad y posición de la particula a medida que pasa el tiempo. Adicionalmente este también se encarga de definir cuando debería explotar la particula, definiendo si se encuentra en una zona llamda explosionThreshold.

<img width="781" height="306" alt="image" src="https://github.com/user-attachments/assets/12b78e35-4e3e-474c-8607-8eb2cacf1166" />

Volviendo a ofApp.cpp observamos que en el método update() se hace un chequeo del frame anterior en cada frame ahí se evalua por cada particula si esta debería de explotar, llamando al metodo shouldExplode() de cada una, si este devuelve true entonces genera un número random entre 0 y 2 para definir que tipo de explosión va a realizar.

<img width="941" height="538" alt="image" src="https://github.com/user-attachments/assets/d8464400-3410-459a-992b-d563cbf062d6" />

Estos tipos de explosiones son objetos que heredan de una clase base llamada ExplosionParticle la cual hereda de Particle. 

Los tipos de particula son los siguientes CircularExplosion, RandomExplosion y StarExplosión, todas tres se diferencian en que forma y con que patrón evolucionan las particulas.

Ya por último se limpia la memoria chequeando si en el frame anterior esa particula estaba muerta.

## 4.  **Consolidación, autoevaluación y cierre:**
> [!CAUTION]
> Esta sección es OBLIGATORIA y central para tu evaluación
