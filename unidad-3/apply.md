# Unidad 3


## 🛠 Fase: Apply

➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿

### 🐟 Actividad 7 🐟

1. __Explicació entre objetos en el stack y en el heap__

Observo que cuando llama las funciones del objeto crea una variable que es una copia del objeto, llamada "this", el problema es que lo hace en ambos casos. sin embargo como pStack es la dirección obtenida directamente y pHeap es el puntero de la direcctión del objeto en el heap entonces creo que pStack es un objeto y pHeap es una referencia a un objeto.

Veo que las direcciones de memoria de pHeap en Locals y en Memory 1 son diferentes, lo que me lleva a pensar que el objeto al que hace referencia está ahí.


➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿

### 🐟 Actividad 8 🐟

__Funciones y objetos en C++__

Entiendo que a CambiarNombre() se le envia una copia de Punto, por eso es que original sigue existiendo, sin embargo no termino de enteneder por que o donde se llama el destructor. Y creería que ambos están en el stack puesto que ninguno es una variable dinámica.

Con el cambio en la función cambiarNombre() observo que ahora p es una referencia y de esa forma cambia los valores reales de la variable que se le entrega, sin embargo sigo sin saber cuando o como funciona ~Punto() entonces voy a buscar.

Ok ya entendrí, es una función que se llama automaticamente en la mayoría de casos, por lo que cuando se tenía cambiarNombre() sin la referencia se destruye puesto que es un objeto que no se va a utilizar mas, sin embargo con referencia el programa de alguna forma sabe que existe por fuera de ese contexto y solo llama su destructor cuando se termina el programa.

Por último cuando se entrega como parámetro el puntero se entiendo que se sobreescribe la posición de memoria de ese objeto, lo digo por que la función ~Punto() solo se llama una vez en todo lo que corre el programa, lo que indica que solo se creó un objeto.


➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿

### 🐟 Actividad integradora de aplicación 🐟

__Código problemático:__

```c++
#include <iostream>
#include <string>

class Personaje {
public:
    std::string nombre;
    int* estadisticas;

    Personaje(std::string n, int vida, int ataque, int defensa) {
        nombre = n;
        estadisticas = new int[3];
        estadisticas[0] = vida;
        estadisticas[1] = ataque;
        estadisticas[2] = defensa;
        std::cout << "Constructor: nace " << nombre << std::endl;
    }

    void imprimir() {
        std::cout << "Personaje " << nombre
            << " [Vida: " << estadisticas[0]
            << ", ATK: " << estadisticas[1]
            << ", DEF: " << estadisticas[2]
            << "]" << std::endl;
    }
};

void simularEncuentro() {
    std::cout << "\n--- Iniciando encuentro ---" << std::endl;
    Personaje heroe("Aragorn", 100, 20, 15);

    Personaje copiaHeroe = heroe;
    copiaHeroe.nombre = "Copia de Aragorn";

    std::cout << "Saliendo del encuentro..." << std::endl;
}

int main() {
    simularEncuentro();
    std::cout << "\nSimulación terminada." << std::endl;
    return 0;
}
```
__Diagnóstico del problema (análisis):__

- __Identifica y explica con detalle al menos dos errores críticos__
  - Los primero que observo que me llamó la atención es que la clase Personaje  no tiene un destructor como en los demás ejercicios, por lo que de alguna forma pienso que esto provoca que haya espacios en la memoria que nunca se liberen, y así, cada que se crean personajes en simular encuentro estos no son eliminados y utilizan espacio de más. Entonces creo que ahí está la principal fuga de memoria.
  - Lo otro que me llama la atención es la siguiente línea: estadisticas = new int[3], puesto que está creando un objeto en el Heap para guardar variables que perfectamente podrían ir en el stack, sin embargo aún no sé esto que implica para el programa como tal, me gustaría ver como se mueve ese espacio de memoria cuando se crea la copia del personaje, sin embargo por ahora solo me parece curioso. Ya después de ver en el depurador observo que ese array estadisticas de hero y copiaHeroe tiene la misma dirección de memoria, entonces creo que para un objeto que se crea en el Heap y se le quiere hacer una copia no basta con simplemente mencionarlo si no crear una copia bien, esto puede ser un problema puesto que ambos objetos le hacen referencia a un mismo espacio de memoria.

    <img width="762" height="55" alt="imagen" src="https://github.com/user-attachments/assets/928d2858-a7be-49b4-8e7d-3ecd204b5631" />


- __Para cada error, describe__
  - ¿Cuál es el error?
    - La clase Personaje no tiene un destructor y por lo tanto solo se libera esa memoria al final.
    - El vector "estadisticas" es el mismo para ambos objetos.
  - ¿Por qué ocurre?
    -  Cómo la clase Personaje no tiene un destructor estos no son destruidos siempre que se sale de un bloque automaticamente sino solo cuando se acaba el programa, esto lo que provoca es que a medida que el programa avanza el espacio de memoria en el stack NUNCA es liberado y por lo tanto a medida que pasa el tiempo la memoria RAM se llena y el programa va más lento.
    -  El vector "estadisticas" tiene una dirección de memoria en el Heap puesto que es una variable dinámica. Esto es una mala práctica puesto que usa el Heap para guardar variables que perfectamente podrían estar en el Stack, esto lo que genera (por alguna razón que desconozco) es que cuando se crea la copia de Aragorn, esta no crea un vector "estadisticas" distinto, sino que coge el valor del puntero "estadisticas" que ya se creó.
  - Consecuencias
    - A medida que pasa el tiempo se come más y más memoria por que no destruye los objetos y eventualmente se queda sin memoria.
    - En este caso si me gustaría imaginarme el caso en el que se crean muchos objetos por que creo que se ejemplifica mejor así. En dado caso de que existan muchos objetos tipo Personaje que son copias de uno entonces todos van a estar haciendo referencia al mismo lugar de memoria en el Heap y esto puede provocar que los atributos de los personajes se dañen puesto que todos usan uno solo. Otra cosa es que no sé muy bien como funcione el destructor pero algo raro debe pasar si todos estos objetos hacen referencia al mismo espacio de memoria.

__Solución y refactorización__

Lo primero sería hacerle un destructor.

Aunque me acabo de dar cuenta que este código solo le da solución a uno de los problemas.

```c++
~Personaje() {
    std::cout << "Destructor: Personaje:" << nombre << ", " << estadisticas[0] << ", " << estadisticas[1] << ", " << estadisticas[2] << std::endl;
 }
```

Por otro lado sería simplemente no utilizar un array y de esa forma nos ahorramos usar espacio en el Heap para variables que pueden estar en el Stack y quedaría algo así, ya tambien con el destructor corregido, yo diría que de esta forma ya no le hace referencia al mismo espacio de memoria, pero la verdad ni idea, hay que ver.

ya vi el depurador y sigo sin saber si eso funcionó, aunque estoy 90% seguro de que si, al menos ya no muestra explicitamente la misma dirección de memoria.

```c++
class Personaje {
public:
    std::string nombre;
    int vida;
    int ataque;
    int defensa;

    Personaje(std::string n, int _vida, int _ataque, int _defensa) {
        nombre = n;
        vida = _vida;
        ataque = _ataque;
        defensa = _defensa;
        std::cout << "Constructor: nace " << nombre << std::endl;
    }

    ~Personaje() {
        std::cout << "Destructor: Personaje:" << nombre << ", " << vida << ", " << ataque << ", " << defensa << std::endl;
     }

    void imprimir() {
        std::cout << "Personaje " << nombre
            << " [Vida: " << vida
            << ", ATK: " << ataque
            << ", DEF: " << defensa
            << "]" << std::endl;
    }
};
```
__CÓDIGO COMPLETO__

```c++
#include <iostream>
#include <string>

class Personaje {
public:
    std::string nombre;
    int vida;
    int ataque;
    int defensa;

    Personaje(std::string n, int _vida, int _ataque, int _defensa) {
        nombre = n;
        vida = _vida;
        ataque = _ataque;
        defensa = _defensa;
        std::cout << "Constructor: nace " << nombre << std::endl;
    }

    ~Personaje() {
        std::cout << "Destructor: Personaje:" << nombre << ", " << vida << ", " << ataque << ", " << defensa << std::endl;
     }

    void imprimir() {
        std::cout << "Personaje " << nombre
            << " [Vida: " << vida
            << ", ATK: " << ataque
            << ", DEF: " << defensa
            << "]" << std::endl;
    }
};

void simularEncuentro() {
    std::cout << "\n--- Iniciando encuentro ---" << std::endl;
    Personaje heroe("Aragorn", 100, 20, 15);

    Personaje copiaHeroe = heroe;
    copiaHeroe.nombre = "Copia de Aragorn";

    std::cout << "Saliendo del encuentro..." << std::endl;
}

int main() {
    simularEncuentro();
    std::cout << "\nSimulación terminada." << std::endl;
    return 0;
}
```
__Justficación de la solución__

- Para el primer caso ya evitamos que los objetos perduren en el tiempo, entonces fácilmente evitamos utilizar memoria constantemente para guardar datos que no se están utilzando.
- En el segundo caso evitamos utilizar el Heap que actúa de forma extraña cuando se intenta copiar un objeto. Utilizamos el stack para manejar esas variables locales de cada objeto y evitar usar variables dinámicas.
