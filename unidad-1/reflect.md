# Unidad 1

## 🤔 Fase: Reflect

♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️

___
___

### 🐟 Actividad 7 🐟

__Parte 1: recuperación de conocimiento__

1) __Describe con tus palabras las tres fases del ciclo Fetch-Decode-Execute. ¿Qué rol juega el Program Counter (PC) en este ciclo?__

   - En la fase de Fetch se cargan los datos del programa a la ROM, en Decode se interpreta esa información del programa y en Execute se realizan las acciones y los movimientos de memoria que indica el programa.
   - El PC toma parte en la parte de Execute, pues indica que instrucción se va a ejecutar a continuación.

2) __¿Cuál es la diferencia fundamental entre una instrucción-A (que empieza con @) y una instrucción-C (que involucra D, M, A, etc.) en el lenguaje ensamblador de Hack? Da un ejemplo de cada una.__

   - La instrucción A la veo como si fuera un indicador de que espacio de memoria se va a modificar o referirse, sin embargo sirve varios propósitos. ej. @KBD.
   - Las instruciones tipo B se refiere a las operaciones que se realizan con los valores de D, M, A. ej. D=D+A.

3) __Explica la función de los siguientes componentes del computador Hack: el registro D, el registro A y la ALU.__

   - __Registro A:__ Funciona como un indicador del espacio de memoria que se va a utilizar, puede ser utilizado como una variable y define a donde se hacen los saltos.
   - __Registro D:__ Funciona como una variable y es la condición con lo que se realizan ifs
   - __ALU:__ Es lo que se encarga de las operaciones que se hacen entre D, A y M[A].

4) __¿Cómo se implementa un salto condicional en Hack? Describe un ejemplo (p. ej., saltar si el valor de D es mayor que cero).__

    - Los saltos condicionales se implementan con las expresiones de tipo D;JXX, donde compara el valor de D con 0, si es igual, diferente, mayor o igual, menor o igual, etc.

5) __¿Cómo se implementa un loop en el computador Hack? Describe un ejemplo (p. ej., un loop que decremente un valor hasta que llegue a cero).__

    - En un espacio de memoria X se va a guardar las iteraciones del programa, una vez empieza el loop se debe de hacer la operación M=M+1, asignarle el valor de M[A] a D con D=M, posteriormente cambiar el valor de A con @Y donde Y es el número de iteraciones que se quiere lograr, hacer la operación D=D-A y si la respuesta es diferente de 0 (D;JNE) entonces hacer el salto a la línea en la qe empieza el loop.

6) __¿Cuál es la diferencia entre la instrucción D=M y la instrucción M=D?__

    - __D=M:__ Este le asigna el valor guardado en la posición A de memoria a D, es lo mismo que D=M[A].
    - __M=D:__ Guarda el valor de D en la posición de memoria A, es decir M[A] = D.

7) __Describe brevemente qué se necesita para leer un valor del teclado (KBD) y para “pintar” un pixel en la pantalla (SCREEN).__

    - __KBD:__ Cuando se presiona una tecla el código del carácter es guardado en la posición 24576 de memoria, entonces para leer ese valor se debe acceder a ese lugar de memoria y guardarlo en D.
    - __SCREEN:__ Para pintar un pixel se debe de acceder a cualquier espacio de memoria entre 16384 y 24576 y cambiar su valor a -1.

___

__Parte 2: reflexión sobre tu proceso__

1) __¿Cuál fue el concepto o actividad más desafiante de esta unidad para ti y por qué?__

    - La actividad 4, principalmente por que no había leído la documentación y se me dificultó la lógica detrás de los loops en el Hack y como organizar las operaciones que se hacen dentro de este.

2) __La metodología de “predecir, ejecutar, observar y reflexionar” fue central en nuestras actividades. ¿En qué momento esta metodología te resultó más útil para entender algo que no tenías claro?__

    - En la actividad 4 ☹️,  por cada cambio que le hacía al programa lo corría para ver si mi lógica era correcta, en la mayoría de los casos no lo fue pero justo eso fue lo que le dio lugar a las mejoras del programa.

3) __Describe un momento “¡Aha!” que hayas tenido durante estas dos semanas. ¿Qué estabas haciendo cuando ocurrió?__

    - ☹️😢😭 Cuando intenté por segunda vez la actividad 4, borré el código en el que trabajé durante el día y volví a intentar haciendo enfasis en la metodología del profe de empezar de atrás para delante, que sirvió bastante, no lo suficiente por que no me salió bien a la primera, de hecho tomó bastantes intentos pero llegó un punto en el que se me ocurrió la forma definitiva de realizar el programa que fue no teniendo procesos separados para el contador de iteraciones y la suma de los números y entonces utilicé el contador para realizar la suma y guardar ese resultado en la dirección de memoria 12. Puede que el ejercicio sea trivial y realmente no hacía falta tanto esfuerzo, pero estoy orgullo de que lo hice por completo yo.

4) __Pensando en la próxima unidad, ¿Qué harás diferente en tu proceso de estudio para aprender de manera más efectiva?__

    - leer la documentación. 
___
___

### 🐟 Actividad 9 🐟

1) __Continuar: ¿Qué aspecto de las actividades, las explicaciones o la dinámica de la clase te ha resultado más útil o te ha gustado más y debería seguir haciendo?__

2) __Dejar de hacer: ¿Qué aspecto de la unidad te ha resultado confuso, poco útil o frustrante? ¿Hay algo que crees que debería eliminar o cambiar drásticamente?__

3) __Empezar a hacer: ¿Qué te habría gustado que hiciéramos que no hicimos? ¿Tienes alguna idea para una actividad o un recurso que podría mejorar el aprendizaje en la próxima unidad?__

4) __Ritmo y Dificultad: en una escala del 1 (muy fácil/lento) al 5 (muy difícil/rápido), ¿Cómo calificarías el ritmo y la dificultad general de esta unidad? ¿Por qué?__

5) __Comentario Adicional: ¿Hay algo más que te gustaría compartir sobre tu experiencia de aprendizaje en esta unidad?__ 
