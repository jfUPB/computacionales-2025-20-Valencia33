# Unidad 2

## 🔎 Fase: Set + Seek

♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️

### 🐠 Actividad 01 🐠

__Dibujando un punto en la pantalla__

```asm
@SCREEN
M=1
@FIN
(FIN)
0;JMP
```

- __¿Que va a pasar?__

  Va a cargar el espacio de memoria que le corresponde al pixel de la esquina superior izquierda y le va a cambiar su valor a 1. lo que volverá ese pixel negro.

- __Reflexiona__

  Sucede que cambia el primer bit de ese espacio de memoria de 16 bits a 1, cambiando solamente el primer pixel, entiendo que cada uno de esos bits corresponde a un pixel en la pantalla. 

- __Traducción a C++__

  Se debe de crear una variable que corresponda a la posición de memoria 16384 y se le debe cambiar su valor a 1.

♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️


### 🐠 Actividad 02 🐠

__Dibujando una línea horizontal__

```asm
@SCREEN
M=-1
@FIN
(FIN)
0;JMP
```
- __¿Que va a pasar?__

  Va a cargar el espacio de memoria que le corresponde al pixel de la esquina superior izquierda y le va a cambiar su valor a -1 de tal forma que todos esos 16 pixeles se vuelven negros.

- __Reflexiona__

  Es verdad que cada uno de esos bits del espacio de memoria @SCREEN corresponde a un pixel en la pantalla.

- __Traducción a C++__

  Se debe de crear una variable que corresponda a la posición de memoria 16384 y se le debe cambiar su valor a -1.

♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️

### 🐠 Actividad 03 🐠

__Entrada salida interactiva__

```asm

@i
M=0
@SCREEN
M=-1

(LEER)
@KBD
D=M

@100
D=D-A
@DERECHA
D;JEQ

@KBD
D=M

@105
D=D-A
@IZQUIERDA
D;JEQ

@LEER
0;JMP

//dirección screen + n

(DERECHA)
//borro la posición actual
@i
D=M
@SCREEN
A=D+A
M=0

//subirle el valor al contador
@i
M=M+1
D=M
@SCREEN
A=D+A
M=-1
@LEER
0;JMP

(IZQUIERDA)
//borro la posición actual
@i
D=M
@SCREEN
A=D+A
M=0

//bajarle el valor al contador
@i
M=M-1
D=M
@SCREEN
A=D+A
M=-1
@LEER
0;JMP

```

- __¿Que va a pasar?__

  - (LEER)
  
  Va a correr un loop que está chequeando constantemente las posición de memoria @KBD y mirando si en algún momento toma los valores 105 y 100 (correspondientes a los carácteres "i" y "d"), cuando eso suceda compara la diferencia de ese valor consigo mismo y con el otro y en caso de que esa diferencia sea 0 entonces salta a la derecha o izquierda dependiendo del valor.

  - (DERECHA)
  
  Al principio va a limpiar el espacio de memoria actual, despues va a sumarle 1 al contador y se lo va a sumar al espacio de memoria el contador, que está siendo guardado en el espacio de memoria @16, y va a cambiar el valor de este lugar de la memoria a -1 y va a realizar un salto a (LEER).

  - (IZQUIERDA)

  Al principio va a limpiar el espacio de memoria actual, despues va a restarle 1 al contador y se lo va a sumar al espacio de memoria el contador, que está siendo guardado en el espacio de memoria @16, y va a cambiar el valor de este lugar de la memoria a -1 y va a realizar un salto a (LEER).

- __Reflexiona__

  Lo útil que es realizar pruebas de los diferentes modulos del programa, de esta forma se pueden encontrar errores puntuales más fácilmente. 

- __Traducción a C++__

  Se me ocurre como hacerlo, sin embargo no conozco suficiente de la sintaxis de C++ para escribirlo en ese lenguaje.

  - Una variable que haga referencia al espacio de memoria donde están los bits correspondientes a la pantalla.
  - Un contador para saber el desfase que hay entre la posición inicial y la actual.
  - Un chequeo para saber que tecla fue presionada, me imagino que C++ siendo más avanzado tendrá una función que lea teclas específicas, a diferencia del Hack.
  - Todo esto dentro de un while.

♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️

### 🐠 Actividad 04 🐠

__Convierte un ciclo while en un ciclo for__

### Ciclo WHILE

__C++__
```c++
//Adds 1+...+100.
 int i=1;
 int sum=0;

 while(i <=100){
    sum+= i;
    i++;
 }
```
__ASM__

```asm
// Adds1+...+100.
 @i // i refers to some memory location.
 M=1 // i=1
 @sum // sum refers to some memory location.
 M=0 // sum=0
 (LOOP)
 @i
 D=M // D=i
 @100
 D=D-A // D=i-100
 @END
 D;JGT // If(i-100)>0 gotoEND
 @i
 D=M // D=i
 @sum
 M=D+M // sum=sum+i
 @i
 M=M+1 // i=i+1
 @LOOP
 0;JMP // GotoLOOP
 (END)
 @END
 0;JMP // Infinite loop
```

### Ciclo FOR

__C++__
```c++
//Adds 1+...+100.
int sum=0;
for(int i = 1; i <=100; i++){
   sum+= i;
}
```

__ASM__
```asm
(LOOP)
@100
M=M+1
D=M
@SUM
M=D+M
@100
D=M
D=D-A
@LOOP
D;JNE
(FIN)
@FIN
0;JMP
```

Ambas llevan un contador en un espacio de memoria, esto para saber el número de iteraciones que lleva o que hay que hacer. En este caso el número de iteraciones en ambos casos es conocido, por lo que no hay diferencia entre el for y el while.

### 🐠 Actividad 05 🐠

__PUNTEROS:__ Son variables que almacenan el espacio de memoria de otra variable.

Ej1.
```C++
int a = 10;
int* p;
p = &a;
*p = 20;
```
- Se crea una variable "a" con valor 10.
- Se inicializa p, que es de tipo int*, que __CREO__ es así pq el espacio de memoria es un entero, ni idea.
- __CREO__ que ese "&" es para referirse al espacio de memoria de "a" en vez de el valor de "a".
- cuando "p" va acompañado de ese asterisco es que le cambia el valor a la variable en ese espacio de memoria (?).

__ENSAMBLADOR__
```asm
@10 //carga el 10
D=A //le asigna 10 a D

@a //crea variable a
M=D // a=10

@a //llama la posición de a
D=A //guarda la posición de la variable a en D
@p //crea variable p
M=D //p= la posición de a

@20 //carga número 20
D=A //lo asigna a D
@p //llama la posición de variable p
A=M //guarda en el registro a lo que estaba almacenado en p (que era la posición de memoria de la variable a)
M=D //reecribe en la memoria de a el valor 20
```

Ej2.
```C++
int a = 10;
int b = 5;
int *p;
p = &a;
b = *p;
```
- En este caso el valor de "b" cambia a 10 puesto que "*p" es igual a "a".

__ENSAMBLADOR__
```asm
@10
D=A

@a
M=D

@5
D=A

@b
M=D

@a
D=A
@p
M=D

//no he terminado esta parte final
@p
A=M
@b
M=D
```


‼️‼️‼️‼️‼️‼️‼️‼️‼️‼️‼️‼️‼️‼️ EXCELENTE EXPLICACIÓN ‼️‼️‼️‼️‼️‼️‼️‼️‼️‼️‼️‼️‼️‼️‼️‼️

### 🐟 NOTAS PARA MIGUEL VALENCIA QUE ESTABA SIENDO MUY JUICIOSO Y PRESENTANDO UNA PRUEBA: 🐟  
`C++:`  
PUNTERO: es una variable que guarda direcciones ✅.  
`int i;` -> i es una variable donde se guarda un valor (un entero). 
  
> `int* ptr;` -> declara un puntero usando * ✅ 
> `ptr = nombre de la variable` ✅ 
> `* = guarda una dirección`  ✅
> `int = el tipo de objetos de los que guarda la dirección.`  ✅
  
> `int i = 5;`  ✅
> `int* ptr = i;` -> NO FUNCIONA!!! no puedes guardar el valor de i en ptr, sólo la posición. Eso es lo que estarías haciendo ahí. ✅

Lo que haría el puntero es APUNTAR al contenido de la variable en la memoria. Para esto se agrega: ✅
> `int* ptr = &i;`, donde & es la definición de la variable. El & lo usamos para llamar la dirección de la variable. Ahí sí estarías guardando su posición. ✅
  
Pero para guardar en una variable el valor de la variable a la que estás apuntando en ese momento en otra variable:  ✅
> `int j = *ptr;`

Y para reescribir la variable a la que estás aputando:✅
> `*ptr = 25;`

🐡 En otras palabras:
> `&i` = para apuntar a la posición de una variable (apuntarle).   ✅
> `*ptr` = para guardar o reescribir el valor que está almacenada en la variable a la que apuntas. ✅

‼️‼️‼️‼️‼️‼️‼️‼️‼️‼️‼️‼️‼️‼️ EXCELENTE EXPLICACIÓN ‼️‼️‼️‼️‼️‼️‼️‼️‼️‼️‼️‼️‼️‼️‼️‼️

