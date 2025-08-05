# Unidad 2


## 🛠 Fase: Apply

♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️

### 🐠 Actividad 06 🐠

__Experimenta con arreglos__

```C++
int arr[] = {1,2,3,4,5,6,7,8,9,10};
int sum = 0;

for (int j = 0; j < 10; j++) {
    sum = sum + arr[j];
}
```
__TRADUCCIÓN A ASM__

```asm
(FOR)
@5 #Posición memoria contador
M=M+1 
D=M #Guarda el contador en D
@15
A=D+A #A le suma el contador para coger la posición de memoria 16.
D=M #Le asigna lo que haya ahí, es decir arr[0]
@FIN
D;JEQ #Necesita que pare cuando M=0
@6 #Posición memoria suma
M=D+M #hace sum += arr[j]
@FOR
0;JMP

(FIN)
@FIN
0;JMP
```
___

- __Predice:__ A=5 le corresponde a la posición de memoria del contador, espacio de memoria que será necesario para saber a que posición del array nos referimos. En el marco del ejercicio este contador parece redundante pues los valores del array van a la par con el contador, sin embargo en caso de que se quieran sumar valores que no son consecuentes en la recta númerica entonces el contador es fundamental. Se carga la posición de memoria 15 puesto que el contador inicia en 1, por lo que al sumar estos dos valores hacemos referencia al lugar de memoria 16, y se le asigna el valor que haya ahí a D (a medida que el contador avanza, se seleccionan valores de A en relación con el anterior). En caso de que ese valor sea 0, significa que el array acabó por lo que va a saltar al final, si ese no es el caso entonces realizará la suma M=D+M y se guardará el resultado en 6 y saltará al principio del FOR.
- __Ejecuta:__ Si pasó eso. 😵‍💫
- __Observa:__ 👁️👁️
- __Reflexiona:__ Me parece que hice un programa más versátil que el del ejercicio, esto debido a que en la actividad propuesta la suma de los valores del array estaba limitada a la condición del FOR (j<10), por lo que si se añade o se quitan valores de ese array entonces no funcionará. En mi programa la suma de los valores del array depende solamente de cuantos valores haya, por lo que se van a sumar los que se hayan inicializado. Si tiene que ser estrictamente cómo el ejercicio indica el único cambio que habría que hacer sería el siguiente:

```asm
@5
D=M
@10
D=D-A
@FIN
D;JEQ
```

El array se debe inicializar desde la posición 16, es decir que M[16]-M[25] serán todos esos números, por lo que para sumarlos se debe de cambiar la posición de memoria dependiendo del contador. Sin embargo, el programa está diseñado de tal forma que suma todos los números que haya en ese array, independientemente de el número de iteraciones, cosa que también se podría chequear.

- __(FOR):__ En la posición 5 de memoria voy a llevar el contador, es decir en algún momento habrá que hacer A=A+D, donde D será el contador. Este contador existe debido a que la posición en el array se consigue con este por medio de A=D+A, lo que logra que nos movamos en la memoria con saltos de a 1. Este FOR es infinito siempre y cuando una posición de memoria en el array no tenga el valor 0... 😐. Igual en el marco del ejercicio este no es el caso, entonces si alguna de esas posiciones es 0 el FOR se para.
- __Inicialización array:__ Cómo indica el ejercicio el array debe ser inicializado desde la posición 16, por lo que este programa permite sumar cualquier número dentro del array siempre y cuando esté antes de un 0.

♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️〰️♾️〰️♾️♾️
