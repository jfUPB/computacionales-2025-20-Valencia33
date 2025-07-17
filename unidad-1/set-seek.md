# _Unidad 1_

## 🔎 Fase: Set + Seek 🔎

### Actividad 01

__🌟 Entender como funciona el cilco fetch-decode-execute 🌟__

- ¿Que es el __fetch__?

Fetch se refiere a recibir una instrucción, es el primer paso en un programa. Basicamente la forma del computador de entender las instrucciones que recibe.

- ¿Que es el __decode__?

El decode se refiere a interpretar aquellas intrucciones para pasarlas a binario, de esa forma el computador entiende a que partes de la memoria debe ir y cuales debe mover

- ¿Que es el __execute__?

El execute ya se refiere de por si a mover aquellas partes de memoria que se le indica en el programa.

```asm
@1
D=A
@2
D=D+A
@16
M=D
@END
(END)
0;JMP
```

__¿Que hace este programa?__

Paso a paso este programa primero con el arroba le asigna el valor 1 a A, posteriormente se le asigna el valor de A a D (D=1), despues se cambia el valor de A con @2, y en la instrucción 4 se le asigna a D el valor de D + A (1+2), despues se le asigna a A el valor de 16 y se guarda en la posición 16 de la memoria (es decir del valor de A) el valor de D, ya por último en @END lo que sucede es que va a la etiqueta de (END) que es la instrucción numero 7, por lo que sería lo mismo que decir que @7 y esto cambia el valor de A. 

#### Experimento 1

- __*¿Qué valor se almacena en la dirección de memoria 16? ¿Por qué crees que es ese valor?*__
  En este pedacito de memoria se va a guardar el valor de D, lo que sucede es que cuando se hace referencia a M este representa un espacio de memoria que corresponde al valor de A
- __*¿Qué cambios observas en el contenido de la memoria y los registros?*__
  Observo que los cambios en la memoria se deben de realizar explicitamente con respecto al valor de A, además en los registros observo como PC cambia dependiendo de que instrucción se va a ejecutar a continuación. Los valores de A cambian por las instrucciones con la arroba y D parece ser puramente de computo.
  

#### Experimento 2

```asm
@5
D=A
@10
D=D+A
@20
M=D
@END
(END)
0;JMP
```

- __*¿Que diferencia hay entre los datos de ROM y RAM?*__
  los datos de RAM son por decirlo de alguna forma "permanentes" es decir, tienen un espacio reservado en lo que se corre el programa. Por otro lado los datos de ROM se refieren a aquellas instrucciones que el computador va a leer, y una vez leidos no los mantiene en la memoria, sin embargo estos si realizan cambios en ella.

### Actividad 2

```asm
@SCREEN
D=A
@i
M=D
(READKEYBOARD)
@KBD
D=M
@KEYPRESSED
D;JNE
@i
D=M
@SCREEN
D=D-A
@READKEYBOARD
D;JLE
@i
M=M-1
A=M
M=0
@READKEYBOARD
0;JMP

(KEYPRESSED)
@i
D=M
@KBD
D=D-A
@READKEYBOARD
D;JGE
@16
A=M
M=-1
@i
M=M+1
@READKEYBOARD
0;JMP
```
#### Experimento 1
Observo en primer lugar que el @SCREEN se refiere a el espacio de memoria 16384, posteriormente pasa a @i, que el computador lo interpreta como @16, y despues el computador tiene una etiqueta que se refiere a las teclas presionadas en el teclado, donde lee el código que le corresponde a la tecla presionada y eso lo guarda en la posición que tenga A en ese momento.

