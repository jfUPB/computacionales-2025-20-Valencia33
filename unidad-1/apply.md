# Unidad 1

## 🛠 Fase: Apply

♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️

### 🐟 Actividad 3 🐟 

#### __Control de flujo con saltos__

Escribe un programa que compare el valor almacenado en la dirección de memoria 5 con el valor 10. Si el valor es menor que 10, guarda el valor 1 en la dirección 7. Si el valor es mayor o igual a 10, guarda el valor 0 en la dirección 7.

El del enunciado:

```asm
(INICIO)
@5
D=M
@10
D=A-D
@MENOR
D;JGE //(D>=0)
@MAYORIGUAL
0;JMP

(MAYORIGUAL)
@7
M=0
@INICIO
0;JMP

(MENOR)
@7
M=1
@INICIO
0;JMP
```

Toma el valor que haya sido introducido en el 5 y se lo da a D, posteriormente A toma el valor de 10 para hacer la comparación de si es mayor o no, esto lo hace de la siguiente forma, al restarle a 10 cualquier número, si este es mayor a 0 entonces significa que el número era menor que 10, sin embargo, si el resultado es negativo o igual a 0 significa que el número es mayor o igual a 10. Partiendo de esto, se utiliza la expresión D;JGE para comprobar si D es mayor o igual a 0, en caso de que si lo sea entonces significa que es menor o igual por lo que procede a guardar 1 en la posición de memoria 7, por otro lado, si este no es el caso entonces guarda un 0 en la posición de memoria 7.

En un principio me pareció confuso realizar comparaciones cuando las únicas expresiones que existen para esas comparaciones son con 0, sin embargo me di cuenta que era todo lo que necesitaba, que solo hacía falta una expresión de más para evaluar la diferencia entre los valores que se quiere comparar.

Este es otro que recibe el código de un carácter y lo compara con 100. Es lo mismo que el anterior pero un poquito más interactivo.

```asm
(INICIO)
@KBD
D=M
@100
D=A-D
@MENOR
D;JGE //(D>=0)
@MAYORIGUAL
0;JMP

(MAYORIGUAL)
@7
M=0
@INICIO
0;JMP

(MENOR)
@7
M=1
@INICIO
0;JMP
```

Este funciona de la misma forma solo que en vez de ingresar un valor en la posición de memoria 5, este está leyendo la posición de memoria que le corresponde a los inputs del teclado y realiza la comparación con 100 en vez de 10.

♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️

### 🐟 Actividad 4 🐟 

#### __Implementación de un ciclo simple__

```asm
(INICIO)
@5
M=M+1
D=M
@12
D=D+M
M=D
@5
D=M
D=D-A
@INICIO
D;JNE
@12
0;JMP
```

El lugar en el que se van a guardar las iteraciones del ciclo es la posición de memoria 5 por lo que al empezar se hace la operación M=M+1 donde se indica que esa sería la primera iteración del ciclo, posteriormente se le asigna ese valor a D. Despues se cambia a la posición de memoria 12, donde se va a guardar el resultado de la suma, allí se realiza D=D+M donde basicamente se suma el número de iteraciones con el acumulado de las sumas y el resultado se guarda en la posición 12. despues se realiza la comparación de si el ciclo ya acabó, utilizando la diferencia entre D (número de iteraciones actual) y A (número de iteraciones total).

Se me dificultó entender el como funcionaba un ciclo, puesto que el manejo de límites de donde suma las iteraciones y como acaba me pareció más confuso y difuso que en otros programas, sin embargo fue una excelente oportunidad para terminar de aprenderme las expresiones de comparación, por que juraba que ese era el problema y no el ciclo. Me ayudó a deducir y eventualmente comprender la lógica detrás de los ciclos.
