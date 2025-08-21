# Unidad 3


## 🤔 Fase: Reflect


♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️

### 🐠 Actividad 11 🐠

__Parte 1: recuperación de conocimiento__

- Explica con tus propias palabras qué es el stack y qué es el heap en C++.
  - Ambos se refieren a espacios de memoria, sin embargo lo que guardan cambia. En el stack se almacenan las variables locales, aquellas como int, float, strings, etc. Por otro lado, en el heap se almacenan variables dinámicas, aquellas que son creadas con el prefijo "new" como objetos, arrays, etc.

- Describe las tres formas de pasar parámetros a una función en C++ (valor, referencia y puntero). Para cada una, explica qué sucede en memoria y cuándo usarías cada método.
  - __*Valor*__ se refiere a pasar solamente el valor de una variable más no la variable como tal, es utilizado cuando se necesita realizar operaciones con ese valor más no cambiarlo en la variable.
  - __*Referencia*__ es cuando se pasa la variable como tal, haciendo referencia al espacio de memoria en el que se encuentra, es utilizado cuando se necesita hacer cambios en la variable, pues este no pasa una copia de ella sino una referencia a ella.
  - __*Puntero*__ se refiere a un tipo de variable que apunta al espacio de memoria donde está guardada la variable a la que se apunta, es utilizada cuando se requiere cambiar el valor de la variable, este sin embargo no crea ninguna copia, edita directamente el valor.

- ¿Qué diferencia hay entre una variable local, una variable global y una variable local estática? ¿En qué segmento del mapa de memoria se almacena cada una?
  - La diferencia entre estas variables es donde están siendo almacenadas, una variable local se almacena en el stack, mientras que las otras dos se almacenan en el espacio de memoria reservado para las globales, estáticas y constantes.

- Explica qué es un objeto en C++ desde la perspectiva de memoria. ¿Dónde se almacenan los miembros de instancia y dónde los miembros estáticos?
  - No tengo la menor idea, asumo que por que es una variable dinámica está guardado en el heap, pero más allá de eso no estoy muy seguro de donde almacene los miembros de instancia y los estáticos.

__Parte 2: transferencia y análisis de situación nueva__

```c++
#include <iostream>
using namespace std;

class Enemigo {
public:
    static int totalEnemigos;
    int vida;
    int* armas;

    Enemigo(int v) : vida(v) {
        totalEnemigos++;
        armas = new int[3];
        armas[0] = 10; armas[1] = 15; armas[2] = 20;
    }
};

int Enemigo::totalEnemigos = 0;

void crearEscuadron() {
    for(int i = 0; i < 5; i++) {
        Enemigo soldado(100);
        soldado.vida -= 10;
    }
    cout << "Escuadrón creado. Total enemigos: " << Enemigo::totalEnemigos << endl;
}

int main() {
    crearEscuadron();
    crearEscuadron();
    return 0;
}
```

- Análisis de problemas: identifica al menos dos problemas
  - Observo que la clase enemigo no tiene un destructor, por lo que a medida que se llama la función crearEscuadron() la memoria se va llenando y no se libera.
  - Noté que la variable armas es un puntero que hace referencia a una variable en el heap, esto es problematico debido a que a medida que se van creando nuevos objetos pertenecientes a esta clase todos van a apuntar a la misma variable que está guardada en el heap, lo cual no es un buen uso de la memoria.
  - totalEnemigos debería ser una variable estática, ya que cada que se crea un enemigo este va a llevar un total de enemigos diferente a los demás, no estoy seguro de si la expresión Enemigo::totalEnemigos arregle ese problema aunque creo que no.

- Predicción de comportamiento: ¿Qué valor mostrará totalEnemigos después de ejecutar el programa? ¿Por qué ocurre esto?
  - Que me pregunten esto me pone nervioso porque creo que ese era uno de los problemas, igual puse tres por que no me gustá que usen un vector pa guardar variables que perfectamente podrían ser locales, que les pasa 😡
  - Olvidenlo no había visto la primera línea de código de la clase, pensé que la estaba inicializando como un int en 0.
  - De igual forma creo que igual va a mostrar un cero, esto debido a que por más que sea estática igual se le está reescribiendo el valor, aunque aún no estoy muy convencido de que sé como funcionan las variables estáticas.

- Propuesta de solución: escribe una versión corregida de la clase Enemigo que solucione los problemas identificados. Explica brevemente cada cambio que hiciste.

Me niego a abrir visual studio para testear.

```c++
#include <iostream>
using namespace std;

class Enemigo {
public:
    static int totalEnemigos = 0; //Inicializar la estática acá arriba, por que solo se pueden inicializar una vez y ya con eso basta.
    int vida;
    int arma0;
    int arma1;
    int arma2;

    Enemigo(int v) : vida(v) {
        totalEnemigos++;
        //armas = new int[3];
        //armas[0] = 10; armas[1] = 15; armas[2] = 20;

        //Acá no estoy muy seguro, estaba convencido de que esto era un error, ya ni idea.
        //En todo caso voy a poner esas variables en el stack.

        arma0 = 10;
        arma1 = 15;
        arma2 = 20
    }

    ~Enemigo() {
      cout << "Enemigo eliminado" << endl;
    }

};

void crearEscuadron() {
    for(int i = 0; i < 5; i++) {
        Enemigo soldado(100);
        soldado.vida -= 10;
    }
    cout << "Escuadrón creado. Total enemigos: " << Enemigo::totalEnemigos << endl;
}

int main() {
    crearEscuadron();
    crearEscuadron();
    return 0;
}
```
Pensandolo mejor creo que hay una mejor forma de solucionar el problema del vector, y es haciendo que "armas" no sea un puntero, si no por valor, de esa forma no todos los objetos creados le hacen referencia al mismo espacio de memoria, igual me niego a aceptar que mi solución de ponerlos en el stack es incorrecta. 😡

__Parte 3: reflexión metacognitiva__

- De todos los conceptos que exploraste en esta unidad (stack vs heap, paso de parámetros, ciclo de vida de objetos, etc.), ¿Cuál consideras que es el más crítico para evitar errores en programas reales? ¿Por qué?
  - Entender el ciclo de vida de los objetos me parece lo más importante, creo que todos seguimos siendo muy ajenos al concepto de memoria, en gran parte por que no es usual utilizar programas que hagan tanto enfasís en eso por lo que pasar de no importar a ser un aspecto fundamental es complejo. No solo eso sino que los objetos por ser variables dinámicas comen mucha memoria, entonces tener un buen manejo de estos es importante para evitar fugas de memoria.
- ¿Cómo cambió tu comprensión sobre lo que realmente es un “objeto” después de comparar C++ con C#? ¿Qué implicaciones prácticas tiene esta diferencia?
  - Ya me parecían cansones en C# ahora tener que manejar su espacio de memoria en C++, yo diría que son las peores noticias que he recibido en 19 años de vida. Pero más allá de eso cambió bastante, más que todo por que siento que se debe ser mucho más estricto y organizado con como se manejan y crean estos objetos, debido a que pueden comer mucha memoria si uno no es cuidadoso. Que puedan existir muchas instancias de un objeto solo complica las cosas por que desde mi punto de vista siempre se debe de estar pensando en dos dimensiones diferentes: Una individual con las variables locales y sus funciones y una global con las variables estáticas, globales y constantes.
- Si tuvieras que explicar a un compañero de semestres anteriores por qué es importante entender la gestión de memoria en programación, ¿Qué le dirías en máximo 3 oraciones?
  - La memoria es aquello que dicta el orden de todas las cosas en un programa, es importante entender la gestión de memoria para evitar que el programa sea más lento y para que sea mucho más rápido y eficiente. 
