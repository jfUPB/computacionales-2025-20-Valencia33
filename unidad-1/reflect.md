# Unidad 1

## 🤔 Fase: Reflect

➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿

### __🐟 Actividad 5 🐟__

#### __*Parte 1: recuperación de conocimiento*__

1. __Describe con tus palabras las tres fases del ciclo Fetch-Decode-Execute. ¿Qué rol juega el Program Counter (PC) en este ciclo?__

   - __Fetch:__ Acá el computador se encarga de cargar las instrucciones del programa, evalua que no haya errores de sintaxis antes de interpretar cada instrucción, y guarda la información en la memoria permanente (en el marco del programa) en la ROM.
   - __Decode:__ En esta fase es cuando el computador interpreta las instrucciones a binario, de esta forma sabrá que partes de la memoria modificar y que valores asignar en la fase execute.
   - __Execute:__ Por último acá es donde lleva a cabo esos movimientos en la memoria, ejecutando el programa y utilizando la memoria temporal RAM.

2. __¿Cuál es la diferencia fundamental entre una instrucción-A (que empieza con @) y una instrucción-C (que involucra D, M, A, etc.) en el lenguaje ensamblador de Hack? Da un ejemplo de cada una.__

    - __Instrucción A__: Este tipo de instrucción me gusta verla como el indicador de que espacio de memoria se va a utilizar, referirse a un espacio de memoria específico, es decir referirse a M y ser la encargada de dictar los saltos en conjunto con las expresiones D;JXX, además son las encargadas de asignarle el valor a A.
  
    - __Instrucción B__: Este tipo de instrucción es diferente de la A pues maneja espacios de memoria efímeros, es decir, cuando se le asigna un valor a D o los espacios de memoria en A, aparte son los encargados de realizar operacionas y mover los datos guardados en la memoria RAM.

3. __Explica la función de los siguientes componentes del computador Hack: el registro D, el registro A y la ALU.__

   - __*El registro D*__ se encarga de tener valores dínamicos y ser una variable independiente tanto para realizar operaciones como guardar datos en la RAM.
   - __*El registro A*__ es un espacio en la memoria ROM que es el encargado de referirse a los espacios en la memoria RAM mientras también trabaja en la ROM.
   - La ALU se refiere a no se, ahora veo.

4. __¿Cómo se implementa un salto condicional en Hack? Describe un ejemplo (p. ej., saltar si el valor de D es mayor que cero).__

   - Para implementar un salto condicional se utilizan las expresiones del tipo D;JXX, estas se encargan de hacer comparaciones del valor de D con 0, sin embargo esto no es suficiente pues en conjunto se debe de utilizar las instrucciones tipo A para indicar a que parte del código se va a realizar el salto, esto es definido con etiquetas que delimiten "funciones" o con el número de la instrucción a la que se quiera saltar. Son utilizados como ifs y para realizar ciclos.

5. __¿Cómo se implementa un loop en el computador Hack? Describe un ejemplo (p. ej., un loop que decremente un valor hasta que llegue a cero).__

   - Para implementar un loop se debe de hacer referencia a un espacio en la memoria donde se va a llevar a cabo el contador del loop, sin embargo existe la posibilidad de que se quiera un loop infinito, en cuyo caso es posible solo usar la expresión D;JMP e indicarle que vaya a la primera línea del ciclo. En cuanto a un loop con cierto número de iteraciones, como dije, se debe de hacer referencia a un espacio de memoria donde se va a llevar el contador, al principio de cada iteración se debe se utilizar la expresión M=M+1, para así subir en uno la iteración e indicar que esa es la primera. Esto tambien se puede hacer al final, la diferencia radica en la expresión de tipo D;JXX que se utiliza para correr de nuevo el ciclo. Una vez se sube el contador del loop, se debe cambiar el valor de A para no afectar el contador y llevar a cabo las operaciones, en caso de que de que sean operaciones que requieran números adicionales al valor de D. En el caso del ejemplo de la pregunta, en este espacio iría el siguiente código: D=M (donde M es el valor que va a decrementar a 0) y posteriormente D=D-1, para saber si se lleva a cabo el salto se utiliza la expresión D;JEQ (if(D=0)) en conjunto con la etiqueta al principio del ciclo.

6. __¿Cuál es la diferencia entre la instrucción D=M y la instrucción M=D?__

   - __D=M[A]__: Esta instrucción le asigna el valor que está guardado en la dirección de memoria M[A], es decir, si A=5 y en ese espacio de memoria está guardado el valor 14, entonces D=14.
   - __M[A]=D__: Esta instrucción le asigna el valor de D al espacio de memoria M[A], es decir, si D=5 y A=9, entonces está expresión va a guardar el valor 5 en el espacio de memoria 9.

7. __Describe brevemente qué se necesita para leer un valor del teclado (KBD) y para “pintar” un pixel en la pantalla (SCREEN).__

    - __valor de teclado (KBD):__ Para leer un valor de teclado se necesita acceder al espacio de memoria 24576, en ese se almacenan los códigos de carácteres cuando una tecla es presionada, es decir, no se guarda permanente mente, una vez se deja presionar el valor de esa dirección de memoria vuelve a 0, para leerlo se necesita realizar la instrucción @KBD o @24576 y asignarle ese valor a D si se quiere guardar.
    - __pantalla (SCREEN):__ Para pintar pixeles de la pantalla, se debe hacer referencia a cualquier espacio de memoria entre 16384 y 24575, cada uno de estos corresponde a un pixel, cambiar sus valores de 0 a 1 provoca que tomen un color negro en la pantalla, en los ejerciciós que hicimos nunca se mantuvo algún valor de esos espacios de memoria, solo se cambiaba su valor.
  
#### __*Parte 2: reflexión sobre tu proceso*__

1. __¿Cuál fue el concepto o actividad más desafiante de esta unidad para ti y por qué?__

   - La actividad más desafiante de esta unidad para mi fue la actividad 4, esto debido a que no había leído la documentación con respecto a los ciclos, no entendía como funcionaban, y me tardé en hacer la distinción entre los ciclos que utilizaban dos espacios de memoria (para la iteración y operaciones) y las que solo utilizan una, eventualmente entendí la diferencia y fue más facíl llevarlo a cabo. Estoy 99% seguro de que el código con el que terminé puede ser mejor, sin embargo cumple su propósito.
  
   - Aparte de eso, como lo mencioné en la parte de Apply, me pareció interesante la forma de hacer saltos e ifs, no me pareció desafiente pero definitivamente me llamó la atención la forma de manejar las comparaciones, pues en algunos casos se necesita un trabajo adicional para comparar esos valores.

2. __La metodología de “predecir, ejecutar, observar y reflexionar” fue central en nuestras actividades. ¿En qué momento esta metodología te resultó más útil para entender algo que no tenías claro?__

   - Lo utilicé en todas las actividades, tanto cuando estaba escribiendo el código como cuando lo ejecutaba por primera vez. En especial me sirvió bastante para la actividad 4, en la que, de nuevo, no entendía como funcionaba el ciclo en ese caso en especial, por lo que fue de gran ayuda ir paso por paso, identificando en que fallaba y corrigiendo. Recuerdo sobretodo que cuando intenté por primera vez esa actividad la predije y corregí paso a paso y fallé en ambas por que termino siendo un programa que sumaba 1 hasta llegar a 5, es decir, no más hice el contador...

3. __Describe un momento “¡Aha!” que hayas tenido durante estas dos semanas. ¿Qué estabas haciendo cuando ocurrió?__

   - Ayer, 23 de Julio a las 9 de la noche intentando resolver la actividad 4, fue un conjunto de cosas, desde empezar de 0, a empezar a construir el ejercicio por partes en vez de hacerlo linealmente, comencé desde el final como recomendó el profe, haciendo la parte de asignar el valor al espacio de memoria 12, despues hacer un ciclo y ya, sin operaciones ni nada adentro, y posteriormente realizar la operación que me pedía, que al final lo hice guardando el acumulado en D y utilizando el contador para ir sumando.

4. __Pensando en la próxima unidad, ¿Qué harás diferente en tu proceso de estudio para aprender de manera más efectiva?__

   - Leer la documentación 😑, y no centrarme tanto en la práctica, que incluso si ese proceso de análisis adicional ayuda bastante, tener en cuenta la teoría y usarla a mi favor podría facilitarme el trabajo, en vez de dar vueltas. Y por último, leer la documentación. 😑😑😑😑😑😑

➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿

### __🐟 Actividad 6 🐟__


