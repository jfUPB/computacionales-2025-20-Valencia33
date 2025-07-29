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

  Va a cargar el espacio de memoria que le corresponde al pixel de la esquina superior izquierda y le va a cambiar su valor a 1 de tal forma que ese pixel ahora se vuelve negro.

- __Reflexiona__

  Sucede que cambia el primer bit de ese espacio de memoria de 16 bits a 1, cambiando solamente el primer pixel, entiendo que cada uno de esos bits corresponde a un pixel en la pantalla. 

- __Traducción a C++__

  Se debe de crear una variable que corresponda a la posición de memoria 16384 y se le debe cambiar su valor a 1.

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

  😟
