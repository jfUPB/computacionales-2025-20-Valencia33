# Unidad 2


## 🤔 Fase: Reflect

🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸

### 🐟 Actividad 07 🐟

__Parte 1: recuperación de conocimiento__

- __Explica cómo se representa y manipula un puntero en el lenguaje ensamblador de Hack. Describe las operaciones equivalentes a p = &a (asignar dirección) y *p = 20 (escribir a través del puntero) usando instrucciones de ensamblador.__

  - En lenguaje de ensamblador hack la forma en la que se representa un puntero es cuando se hace referencia a un espacio de memoria en específico, por lo que sería cuando se utilizan este tipo de instrucciones @D. El equivalente de p=&a en hack sería @20, D=A. y de p=&a sería @20, D=M.

- __¿Cómo implementarías el acceso a un elemento de un arreglo, como arr[j], en lenguaje ensamblador? Describe el rol de la dirección base del arreglo y el índice j en esta operación.__

  - En este caso supongamos que los elementos del arreglo están inicializados desde la posición de memoria 16, en cuyo caso, para representar j se debe de hacer lo siguiente.

```asm
//suponiendo que ya está inicializado
@16
A=D+A
//donde D es la posición de j en el array
```

__Parte 2: reflexión sobre tu proceso__

- __¿Cuál fue el concepto más abstracto o difícil de “traducir” de C++ a ensamblador en esta unidad (punteros, ciclos, arreglos)? ¿Qué hiciste para lograr entenderlo?__

  - El concepto más complejo de entender en esta unidad fue el de los punteros, no por que fuera abstracto, sino por que fue un concepto totalmente nuevo a diferencia de los otros. Entenderlo no fue complejo pero si requirió un mayor esfuerzo para comprender la lógica detrás de este.

- __En la Actividad 06 se sugirió construir el programa “PASO A PASO mediante pruebas”. ¿Cómo te ayudó este enfoque a manejar la complejidad del problema?__

  - Esta metodología de dividir el problema en diferentes "módulos" fue excelente para la resolución de las actividades, esto debido a que permite concentrarse en partes más simples del programa, fue mucho más facil que las demás actividades.

- __Esta unidad fue el “puente” hacia C++. ¿Qué concepto de bajo nivel te sientes más seguro de poder identificar cuando lo veas implementado en C++?__

  - Yo diría que todos son bastante simples de implementar entonces realmente todos, sin embargo el concepto de punteros si siento que puede tener un nivel de dificultad mayor.


🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸

### 🐟 Actividad 08 🐟

[Bitácora de Mar Torrente](https://github.com/jfUPB/computacionales-2025-20-EsTorrente/blob/unidad2/apply/unidad-2/apply.md)

```asm
@i
M=0

(ARREGLO)
//subir contador
@i
M=M+1

D=M
A=D
M=D

//check arreglo
@10
D=D-A
@ARREGLO
D;JLT

@i
M=0
@SUMA
0;JMP

(SUMA)
@i
D=M
@sum
M=D+M

//CHECK
@9
D=D-A
@FIN
D;JGT

//SUBIR CONTADOR
@i
M=M+1
@SUMA
0;JMP

(FIN)
@FIN
0;JMP
```
- Correrlo sin ninguna modificación en la memoria RAM.

  - Esto con el fin de chequear que efectivamente el programa hace lo que indica el ejercicio.
  - El código funciona perfectamente y cumple con lo que pedía el ejercicio.

- Realizar cambios en la memoria RAM.

  - Esto lo tengo pensado hacer para ver cómo el programa trata con eso cambios en la memoria, ver si los reescribe o si rompe el programa por completo. Esto con el fin de evaluar la versatilidad y repeteción del programa.
  - El programa reescribe la posición de memoria cada que llega a ella y no depende de que haya 0s en todas las posiciones de memoria, es decir, no solo es un programa que cumple con lo pedido sino que además toma en cuenta otras posibilidades en el marco del computador Hack.


🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸

### 🐟 Actividad 09 🐟

- __Continuar: ¿Qué actividad, problema o explicación de esta unidad te ayudó más a entender la conexión entre el bajo y el alto nivel? ¿Qué debería mantener sin cambios?__

  - Me encantó la actividad del array y de la traducción del for y el while a lenguaje ensamblador, me pareció necesaria, no solo para hacer la transición a C++ sino tambien para darle sentido a todas esas operaciones que hemos estado viendo en el lenguaje ensamblador.

- __Dejar de hacer: ¿Hubo alguna actividad o concepto que te pareció redundante, demasiado confuso o que aportó poco valor a tu aprendizaje? ¿Qué eliminarías o modificarías?__

  - Ninguno realmente, todas las actividades de esta unidad me parecieron cruciales.

- __Empezar a hacer: ¿Qué idea tienes para mejorar la próxima unidad? ¿Hay algún tipo de recurso que te habría ayudado a entender mejor los punteros o los arreglos?__

  - Me gustan mucho las actividades que son traducir, aunque me imagino que la siguiente unidad es C++ del todo, entonces de pronto esa modalidad no es posible. En general me gustan las actividades autonomas.

- __Ritmo y Dificultad: en una escala del 1 (muy fácil/lento) al 5 (muy difícil/rápido), ¿Cómo calificarías el salto de dificultad de la Unidad 1 a la Unidad 2? ¿El ritmo fue adecuado? Justifica tu calificación.__

  - Un 3, pero más que todo por que sigue siendo muy nuevo, no por que haya faltado explicación ni nada, la fase apply me parece fundamental y en gran parte es lo que hace que no sea tan pesado el cambio.

- __Comentario Adicional: ¿Alguna otra cosa que quieras compartir sobre cómo te sentiste aprendiendo estos conceptos?__

  - Contento, me gustó la unidad.

