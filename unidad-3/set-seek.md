# Unidad 3

## 🔎 Fase: Set + Seek

♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️

### 🐠 Actividad 01 🐠

__Hola mundo__

Voy a copiar todo pq no sé que sabes y que no sabes.

__El profe dijo que no todas las actividades de esta unidad eran necesarias pero que si sería bueno que las hicieramos todas por nuestra cuenta__

- std::cout es un objeto que se refiere a character output, se le puede enviar de todo concatenando las instrucciones con este cosito: <<. Sirve para enviar datos a la consola para ser impresos como textos. Para utilizarlo tienes que incluir la librería que contiene el cosito que es: #include <iostream>.
  
<img width="718" height="308" alt="image" src="https://github.com/user-attachments/assets/e27cecf5-3af4-4b5d-b901-b85f639acf6a" />

- nos mostró esto para ver como es esa traducción de lenguaje de máquina a alto nivel y nos habló de que a la hora de asignar variables ambas instrucciones tienen cositas en común.

- Nos enseñó a usar el depurador. Muy intuitivo, lo único es que el step over lo que hace es que se salta las funciones y el step si va línea por línea.
  
  <img width="208" height="39" alt="image" src="https://github.com/user-attachments/assets/a298b967-dd3c-4881-935d-1108ba8cdfea" />

- Todo esto no más es como pa la parte de predecir, el menciona que lo más bacano es usar esta ventana:

  <img width="937" height="823" alt="image" src="https://github.com/user-attachments/assets/d6beeab7-70c0-4b0c-a286-bcc6839302af" />

- Que sirve para ver el nombre, tipo y valor de cada variable con respecto a una línea del código, es muy divertido.

no ha dicho absolutamente nada que no esté en la página.

♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️

### 🐠 Actividad 02 🐠

```c++
#include <iostream>

using namespace std;

// Función que modifica el parámetro pasado por valor
void modificarPorValor(int n) {
    cout << "Dentro de modificarPorValor, valor inicial: " << n << endl;
    n += 5;
    cout << "Dentro de modificarPorValor, valor modificado: " << n << endl;
}

// Función que modifica el parámetro pasado por referencia
void modificarPorReferencia(int &n) {
    cout << "Dentro de modificarPorReferencia, valor inicial: " << n << endl;
    n += 5;
    cout << "Dentro de modificarPorReferencia, valor modificado: " << n << endl;
}

// Función que modifica el parámetro utilizando punteros
void modificarPorPuntero(int *n) {
    cout << "Dentro de modificarPorPuntero, valor inicial: " << *n << endl;
    *n += 5;
    cout << "Dentro de modificarPorPuntero, valor modificado: " << *n << endl;
}

int main() {
    int a = 10;
    int b = 10;
    int c = 10;

    cout << "Valor inicial de a (paso por valor): " << a << endl;
    cout << "Valor inicial de b (paso por referencia): " << b << endl;
    cout << "Valor inicial de c (paso por puntero): " << c << endl;

    cout << "\nLlamando a modificarPorValor(a)..." << endl;
    modificarPorValor(a);
    cout << "Después de modificarPorValor, valor de a: " << a << endl;

    cout << "\nLlamando a modificarPorReferencia(b)..." << endl;
    modificarPorReferencia(b);
    cout << "Después de modificarPorReferencia, valor de b: " << b << endl;

    cout << "\nLlamando a modificarPorPuntero(&c)..." << endl;
    modificarPorPuntero(&c);
    cout << "Después de modificarPorPuntero, valor de c: " << c << endl;

    return 0;
}
```
- __modificarPorValor()__

  - Recibe como párametro una copia de esa variable, es decir realmente no módifica la variable que se pasa cuando se llama la función.

- __modificarPorReferencia()__

  - Acá el parámetro es "int& n" que es la referencia de una variable, en el paso anterior n se refería a una copia de la variable que se le pasó, en este caso hace referencia a la variable como tal.

- __modificarPorPuntero()__

  - Acá si recibe la dirección de memoria de la variable, no modifica el espacio de memoria pues la instrucción es *n+=5.

__Ejercicio de intercambiar por valor, referencia y punteros__

Nos puso a hacer este ejercicio por que acá la diferencia entre esos parámetros es más evidente y es mucho más fácil identificar las diferencias entre esas "notaciones".

```c++
#include <iostream>

using namespace std;

void swapPorValor(int a, int b)
{
    int cambio = b;
    b = a;
    a = cambio;
}

void swapPorReferencia(int& a, int& b)
{
    int cambio = b;
    b = a;
    a = cambio;
}

void swapPorPuntero(int* a, int* b)
{
    int cambio = *b;
    *b = *a;
    *a = cambio;
}

int main() {
    int a = 12;
    int b = 15;

    cout << "Valor inicial de a: " << a << endl;
    cout << "Valor inicial de b: " << b << endl;

    cout << "\nLlamando a swapPorValor..." << endl;
    swapPorValor(a, b);
    cout << "Despues de swapPorValor, valor de a, b: " << a << ", " << b << endl;

    cout << "\nLlamando a swapPorReferencia..." << endl;
    swapPorReferencia(a, b);
    cout << "Despues de swapPorReferencia, valor de a, b: " << a << ", " << b << endl;

    cout << "\nLlamando a swapPorPuntero..." << endl;
    swapPorPuntero(&a, &b);
    cout << "Despues de swapPorPuntero, valor de a, b: " << a << ", " << b << endl;

    return 0;
}
```
♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️

### 🐠 Actividad 04 🐠

__Experimentos__

1. __modificar el segmento de texto__

  ```c++
#include <iostream>
#include <cstdlib>

using namespace std;


int main() {
    // Variable local (stack)
    int a = 10;
    int b = 20;

    /**********************************************************
        EXPERIMENTO 1
    ***********************************************************/

    void* ptr = reinterpret_cast<void*>(&main);
    cout << "Voy a modificar la memoria en la dirección: " << ptr << endl;
    *reinterpret_cast<int*>(ptr) = 0;

    /********************************************************/

    return 0;
}
  ```

- __Predicción__

En este caso se crea una variable tipo void* llamada ptr, y se le __intenta__ asignar un valor, debido a que se intenta castear el valor de main a un void*.

Posteriormente se saca un texto donde menciona la dirección de memoria de este ptr.

Y por último se "reinicia" la variable.

- __¿Qué ocurre? ¿Por qué?__

Todo bien excepto que no sabía que iba a dar error. Esto ocurre pues intenta sobrescribir el valor de una función que está en el __segmento de texto__.

3. modificar el segmento de datos (variables globales)

  ```c++
#include <iostream>
#include <cstdlib>

using namespace std;

// Variables globales
int global_inicializada = 42;
int global_no_inicializada;


int main() {
    // Variable local (stack)
    int a = 10;
    int b = 20;

    /**********************************************************
        EXPERIMENTO 3
    ***********************************************************/

    cout << "global_inicializada: " << global_inicializada << endl;
    cout << "global_no_inicializada: " << global_no_inicializada << endl;


    global_inicializada = 69;
    global_no_inicializada = 666;

    cout << "global_inicializada: " << global_inicializada << endl;
    cout << "global_no_inicializada: " << global_no_inicializada << endl;

    /********************************************************/

    return 0;
}
  ```

De este experimento me llevo que una variable no inicializada se le da un valor por defecto de 0. Intenté y se pueden realizar operaciones con variables no inicializadas, muy raro pensé que daría error.

♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️

### 🐠 Actividad integradora de la investigación 🐠

__analizar un programa integral, predecir su comportamiento en memoria y verificar tus hipótesis utilizando el depurador de Visual Studio.__

```c++
#include <iostream>

int contador_global = 100;

void ejecutarContador() {
    static int contador_estatico = 0;
    contador_estatico++;
    std::cout << "  -> Llamada a ejecutarContador. Valor de contador_estatico: " << contador_estatico << std::endl;
}

void sumaPorValor(int a) {
    a = a + 10;
    std::cout << "  -> Dentro de sumaPorValor, 'a' ahora es: " << a << std::endl;
}

void sumaPorReferencia(int& a) {
    a = a + 10;
    std::cout << "  -> Dentro de sumaPorReferencia, 'a' ahora es: " << a << std::endl;
}

void sumaPorPuntero(int* a) {
    *a = *a + 10;
    std::cout << "  -> Dentro de sumaPorPuntero, '*a' ahora es: " << *a << std::endl;
}

int main() {
    int val_A = 20;
    int val_B = 20;
    int val_C = 20;

    std::cout << "--- Experimento con paso de parámetros ---" << std::endl;
    std::cout << "Valor inicial de val_A: " << val_A << std::endl;
    sumaPorValor(val_A);
    std::cout << "Valor final de val_A: " << val_A << std::endl << std::endl;

    std::cout << "Valor inicial de val_B: " << val_B << std::endl;
    sumaPorReferencia(val_B);
    std::cout << "Valor final de val_B: " << val_B << std::endl << std::endl;

    std::cout << "Valor inicial de val_C: " << val_C << std::endl;
    sumaPorPuntero(&val_C);
    std::cout << "Valor final de val_C: " << val_C << std::endl << std::endl;

    std::cout << "--- Experimento con variables estáticas ---" << std::endl;
    ejecutarContador();
    ejecutarContador();
    ejecutarContador();

    return 0;
}
```

- __¿Cuál será la salida final en la consola de este programa?__

  - En un principio va a mostrar el valor guardado en A, posteriormente llamará la función SumaPorValor() y le entregará como parametro val_A, que como aprendimos en realidad es una copia de la variable inicializada en la memoria stack. Dentro de esta función se le sumará 10 al valor que entregó "a", por lo que en la consola escribirá: __Dentro de sumaPorValor, 'a' ahora es: 30__, sin embargo esto no cambiará el valor de val_A puesto que no se modificó el valor en el espacio de memoria de esta variable, solo el de la copia.
  - En el caso de B esto es diferente, puesto que es por referencia entonces no le pasa una copia sino la variable de verdad, por lo que la operación que se realiza dentro de la función si afecta el valor de la variable val_B. El nuevo valor será 30.
  - En este caso tambien se modifica el valor de la variable entregada, sin embargo lo hace diferente, puesto que recibe el espacio de memoria de la variable y eso es lo que manipula realmente, provocando que el resultado final sea 30.
  - Por último están esas tres llamadas a la función ejecutarContador(), en este caso si se aumentaría el contador hasta 3, incluso si parece que reescribe la variable varias veces este no es el caso puesto que una variable estática solo se puede inicializar una vez.

- __Escribe la salida completa que esperas.__

  - val_A: 20
  - val_B: 30
  - val_C: 30
  - contador_estatico: 3

- __Dibuja un mapa de memoria conceptual de este programa__

  
