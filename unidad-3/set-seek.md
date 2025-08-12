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
