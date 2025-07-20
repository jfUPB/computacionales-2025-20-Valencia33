# _Unidad 1_

## 🔎 Fase: Set + Seek 🔎

➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿

### 🐟 Actividad 1 🐟

__🌟 Entender como funciona el cilco fetch-decode-execute 🌟__

- ¿Que es el __fetch__?

Fetch se refiere a recibir una instrucción, es el primer paso en un programa. Basicamente la forma del computador de entender las instrucciones que recibe.

- ¿Que es el __decode__?

El decode se refiere a interpretar aquellas intrucciones, de esa forma el computador entiende a que partes de la memoria debe ir y cuales debe mover

- ¿Que es el __execute__?

El execute ya se refiere de por si a la instrucción como tal, a llevarla a cabo y a mover aquellas partes de memoria que se le indica en el programa.

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

🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹

#### ⚗️ Experimento 1 ⚗️

- __*¿Qué valor se almacena en la dirección de memoria 16? ¿Por qué crees que es ese valor?*__
  
  En este pedacito de memoria se va a guardar el valor de D, lo que sucede es que cuando se hace referencia a M este representa un espacio de memoria que corresponde al valor de A
- __*¿Qué cambios observas en el contenido de la memoria y los registros?*__
  
  Observo que los cambios en la memoria se deben de realizar explicitamente con respecto al valor de A, además en los registros observo como PC cambia dependiendo de que instrucción se va a ejecutar a continuación. Los valores de A cambian por las instrucciones con la arroba y D parece ser puramente de computo.
  
🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹

#### ⚗️ Experimento 2 ⚗️

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
  
  los datos de RAM son por decirlo de alguna forma datos "temporales", tienen un espacio reservado en lo que se corre el programa. Por otro lado los datos de ROM se refieren a aquellas instrucciones que el computador va a leer, es decir a diferencia de la RAM, la ROM almacena esa serie de instrucciones permanentemente.

🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹

➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿

### 🐟 Actividad 2 🐟

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
🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹

#### ⚗️ Experimento 1 ⚗️

1) Observo en primer lugar que el @SCREEN se refiere a un espacio de memoria, en este caso es 16384, posteriormente pasa a @i, que tambien se refiere a un espacio de memoria pero esta vez es 16. Despues se refiere a @KBD que tambien es un espacio en la memoria, esta vez es 24576, aún no sé a que corresponden estos estas partes de la memoria.

2) más allá de esas asignaciones en la memoria vi algo que me llamó la atención que me confundió al principio pero que tiene todo el sentido del mundo y es que cuando indica la instrucción D=M, el valor de D = 0, sin embargo lo que entiendo es que ese espacio de memoria no tenía ningún valor y que confundí el valor de A con la posición a la que se está refiriendo.

3) También me llamó la atención la línea que dice D;JNE, y viendo la documentación descubrí que esa expresión funciona como un if, hay muchas más y las voy a poner acá más adelante pero esta en especifico sería en C# como: __if(D!=0) { }__. 

```asm
@D;JGT //If out > 0 jump
@D;JEQ //If out = 0 jump
@D;JGE //If out >= 0 jump
@D;JLT //If out < 0 jump
@D;JNE //If out != 0 jump
@D;JLE //If out <= 0 jump
@D;JMP //jump
```
y otra cosa que me pareció relevante fue lo siguiente: 

> he last instruction (0;JMP) effects an unconditional jump. Since the C-instruction
syntax requires that we always effect some computation, we instruct the ALU to
compute 0 (an arbitrary choice), which is ignored.

eso y también lo que implica el campo "jump":

>jump implies ‘‘continue execution with the instruction
addressed by the A register.’’

__y ya en el marco del código que estamos analizando veo que como D=0 no va a saltar a la instrucción 20.__

4) En la instrucción 13 está D;JLE que sería como decir __if(D<=0) {}__. entonces lo que pienso que va a pasar es que como D=0 este va a saltar a la instrucción número 4. Teniendo esto en cuenta yo creo que se puede afirmar que el programa es un bucle infinito, sin embargo me gustaría ver que pasa si una de esas condiciones que propone se cumple.
   
5) Ahí cacharreandole más a la documentación vi que cuando el teclado está activado este recibe la tecla presionada por su código ASCII en binario y lo guarda en el espacio de memoria 24576, entonces supongo que si presiono una tecla cuando indica que D=M entonces D tomará un valor diferente a si no presiono ninguna tecla. Con esto entonces puedo decir que @SCREEN y @KBD corresponden a los lugares en la RAM 16384 y 24576 respectivamente y encima que son la memoria de la pantalla y el teclado.
   
6) En caso de que una tecla esté siendo presionada este valor va a cambiar el espacio de memoria 24566 por el código del carácter. Esto va a provocar que en el check que se hace en la línea 7 se dispare y salte a la línea 20 pues A=20, allí el valor de A será igual a 16 (que es el espacio de memoria donde originalmente se guardó el valor 24576, que vale la pena recordar es el espacio de memoria que corresponde a la pantalla) y le asignará a D el valor que está guardado ahí para despues cambiarle el valor a A a ese mismo número y restarlos, despues A será igual a 4 y se chequea si el valor de D es menor o igual a 0, si no lo es seguirá derecho y empezará a cambiar el valor de los espacios de memoria >= 16384 a -1, para volver esos pixeles negros, siempre y cuando esté presionada.

🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹🔹

- __¿Que hacen las instrucciones ALU?__

  una instrucción que utilice la Arithmetic Logic Unit (ALU) puede ser en la línea D=D-A debido a que tiene como entrada dos valores y entrega uno, en este caso está agarrando el valor de D que fue definido por D=M[A] y posteriormente el valor de A que fue definido por @16384 y los resta para asignarle el valor a D que sería 0.

- __¿Para qué sirve el registro PC?__

  El registro PC sirve para saber que instrucción se ejecutará a continuación, normalmente es consecutivo aunque se puede direcionar a otra parte utilizando una de las expresiones que puse antes y el valor de A.

- __¿Cuál es la diferencia entre @i y @READKEYBOARD?__

  @i se refiere a un espacio de memoria predeterminado mientras que @READKEYBOARD hace referencia a la etiqueta del mismo nombre que está en la línea 4 y por lo tanto le asigna ese mismo valor a A para posteriormente hacer un salto a esa posición, entonces es decir que @i es predeterminado a ser 16 mientras que la etiqueta perteneciente a @READKEYBOARD puede estar en cualquier parte.

- __¿Qué se necesita para leer el teclado y mostrar información en la pantalla?__

  Es necesario saber que cualquier input del teclado lo recibe este computador en el espacio de memoria 24576 donde guarda su código ASCII como el número que le corresponde a cada carácter en 16-bits. Si ese valor es != 0 entonces el chequeo que hace de D;JNE ( if(D != 0) { jump(KEYPRESSED) ) donde se corre un loop que solo se rompe si el valor de D vuelve a ser cero, en este loop lo que se hace es que se corre por cada posición de memoria superior a 16384 (es decir la memoria que corresponde a la memoria) y se cambia su valor por -1 haciendo que la pantalla cambie gradualmente a negro. En conclusión, para leer el teclado se necesita acceder al espacio de memoria 24576 y para mostrar información en pantalla se debe de cambiar los valores de la memoria mayores a 16384.

- __¿Existe un bucle en el programa? ¿Que hace?__

  El bucle que chequea la posición de memoria 24576 a ver si es cero, este bucle se encarga de orquestar que va a suceder, pues que M[24576] = 0 significa que no hay ningún input del teclado, sin embargo cuando si haya este valor cambiará y será enviado a otro loop que solo se rompe si M[24576] vuelve a ser 0.

- __¿Hay condiciones en el programa? ¿Que hace?__

  Si, de hecho hay varias y son utilizadas de varias formas, principalmente para romper los loops, sin embargo hay una que se encarga de devolver todos los espacios de memoria < M[24576] a 0, me refiero a la condición en la línea 13 que se encarga de chequear si D es menor o igual a 0, como esto no es cierto hasta que M[16384] sea 0 entonces se crea una especie de while.

