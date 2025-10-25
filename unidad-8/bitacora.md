# Bitácora de aprendizaje de la unidad 8

## Actividad 1

- **Ejecuta el programa y haz clic en la ventana. Observa lo que sucede. ¿Qué es lo que ves? ¿Qué es lo que esperabas ver? ¿Por qué crees que sucede esto?**

  - Observo un circulo que se mueve de izquierda a derecha y que cuando se presiona el click cambia de tamaño, sin embargo sucede que al cambiar de tamaño la aplicación para. creo que esto sucede por que hay un proceso muy pesado para calcular el tamaño nuevo del circulo.

- **Observa que el programa ahora no se congela, pero el círculo no cambia de tamaño inmediatamente. ¿Por qué crees que sucede esto? ¿Qué es lo que está pasando?**

  - Pues observo que sobreescribe la funci[on threadedFunction para añadir heavyComputation(), y me imagino que esa biblioteca, llamando esa método se encargará de moverla a otro hilo. Para darle razón a la demora en el cambio del tamaño del circulo diría que tiene algo que ver con el resto de llamados de las demás funciones y CREO que el culpable de esto es lock() que como explicó el profe se utiliza para evitar condiciones de carrera, por lo que creo que obliga a que solo el hilo principal lo ejecute cuando acabe.

- **En tus propias palabras, explica la diferencia entre concurrencia y paralelismo. ¿Por qué es importante entender esta diferencia al trabajar con hilos?**

  - La diferencia entre estos dos conceptos es que la concurrencia realmente es hacer un poco de muchas tareas en poco tiempo para dar la sensación de que se hacen al mismo tiempo, paralelismo realmente realiza las tareas al mismo tiempo. Esta diferencia es fundamental puesto que un hilo puede ser concurrente y realizar varias tareas pero para que sea paralelismo se tienen que usar varios hilos. 

## Actividad 2

- **Según lo que te he venido comentando, los hilos te permiten ejecutar tareas en paralelo; sin embargo, piensa qué ocurre con el paralelismo cuando se sincroniza el acceso a un recurso compartido. ¿Qué ocurre con el rendimiento del programa? ¿Es posible que el rendimiento se vea afectado por el uso de mutex? ¿Por qué?**

  - El profe ya me hizo spoiler y lo que se sucede es que se puede prestar para que se den considicones de carrera, lo que significa que no, el rendimiento no se ve afectado pero si se pueden dar errores puesto que hay varios hilos trabajando con datos diferentes que en últimas afectan el resultado del recurso compartido. La solución de esto es el mutex, que lo que hace es que solo deja que un hilo edite el valor del 

- **Ejecuta el código y observa el resultado. ¿Qué ocurre si cambias el valor de la variable useLock? ¿Por qué crees que ocurre esto?**

  <img width="447" height="160" alt="image" src="https://github.com/user-attachments/assets/d16376d4-ca80-43d6-bced-1ec2bec5f702" />
  <img width="421" height="149" alt="image" src="https://github.com/user-attachments/assets/b79b54cf-a3fb-4780-94b6-8fc9e14e741d" />

  - Ocurre esto precisamente por que hay varios hilos agarrando el mismo valor de counter y escribiendo el mismo valor dos veces, y eso a gran escala provoca que jamás se llegue al valor esperado.

- **Explica en tus propias palabras ¿Cómo puede presentarse la condición de carrera en este caso? ¿Qué es lo que está pasando? Te pido que propongas un ejemplo.**

  - Está pasando que hay un hilo que va y mira el valor de counter, que digamos es 10, pero en ese mismo instante otro hilo agarra ese mismo valor sin que el otro lo haya actualizado, lo que significa que ambos van a escribir 11 en la memoria, lo que si, digamos el valor esperado es 20, provoca que en últimas este sea 19. 

## Actividad 3

<img width="1019" height="762" alt="image" src="https://github.com/user-attachments/assets/9f6196f5-978f-4ce3-9e3a-7896797c26f3" />

<img width="1022" height="765" alt="image" src="https://github.com/user-attachments/assets/08ae8091-ec19-48fe-8ec7-1dcb045e550b" />

Absolutamente nada que ver pero quise poner maxIterations en 1 para ver como lentamente se iba formando el fractal y ver que valores divergen inmediatamente.

<img width="1018" height="762" alt="image" src="https://github.com/user-attachments/assets/5a280afc-29e9-4366-a463-70f4fd80a5fa" />

<img width="1017" height="764" alt="image" src="https://github.com/user-attachments/assets/c5d48c92-ff9b-43c1-81c8-a7b5e80ba9ad" />

<img width="1017" height="761" alt="image" src="https://github.com/user-attachments/assets/56d96501-62e1-4f99-bea5-2648c205b2be" />

<img width="1024" height="766" alt="image" src="https://github.com/user-attachments/assets/15a08161-d49d-454f-ad1c-f4171f4bb262" />

<img width="1024" height="761" alt="image" src="https://github.com/user-attachments/assets/b3d5db3f-6779-4d01-a5c5-1f74ac8ff956" />

Ya si seriamente vi esta linea de acá: numThreads = std::thread::hardware_concurrency(), el valor que devuelve es 16 correspondiente a los cores de mi cpu, sin embargo, la diferencia de tiempo de computo entre un solo hilo y 16 es menos de 0.1s entonces me pareció curioso que esa diferencia fuera pequeña, entonces la pregunta que tengo es que si hay programas donde utilizar tantos threads realmente sea un consumo innecesario de recursos cuando solo uno es más que suficiente, en este seguramente no es el caso pero me surgió la duda y ahora quiero hacer la comparación. Y también saber que pasa internamente cuando manualmente hago que este número sea >16.

Mi hipotesis es que va a ser igual o más lento que lo que ya es, lo digo por que o puede ignorar por completo esos cores inexistentes o usar los que ya están pero que no sea en paralelismo, en cualquier caso no creo que haya una mejora en rendimiento.

16 threads: 
<img width="346" height="118" alt="image" src="https://github.com/user-attachments/assets/f41d6c71-6293-46b1-abac-2b409544b203" />

64 threads: 
<img width="348" height="113" alt="image" src="https://github.com/user-attachments/assets/71d2e4e6-1fc6-4035-a333-f3e4e0dd2be0" />
<img width="344" height="115" alt="image" src="https://github.com/user-attachments/assets/3fb24443-e67e-4b0d-87f9-b3c8aee8a0d1" />
<img width="345" height="117" alt="image" src="https://github.com/user-attachments/assets/e27d522d-294f-45a9-b69d-2554cc41e3e6" />

juzgando por la diferencia de tiempos CREO que no ignora el hecho de que numThreads sea >16, sino que ya lo que está pasando es que si hay una condición de carrera con aquellos nuevos que utiliza y por eso es tan volatil.

## Actividad 4

- **1.) ¿Cuál es la estructura de datos principal que contiene la información de todos los boids y que es accedida por múltiples hilos (el hilo principal para dibujar, el hilo trabajador para actualizar)?**

  -  Dentro de flock está el vector que contiene todos los boids
  -  <img width="246" height="259" alt="image" src="https://github.com/user-attachments/assets/c3ddf288-da81-4f22-8f33-f06233a945df" />

- **2.) Observa la función Flock::threadedFunction() donde el hilo trabajador calcula el movimiento. ¿Qué operaciones realizan sobre el vector de boids compartido?**

  - <img width="313" height="84" alt="image" src="https://github.com/user-attachments/assets/dcd90758-6f02-4555-bacc-3fb188b8c62f" />
  - <img width="415" height="421" alt="image" src="https://github.com/user-attachments/assets/b412ccc4-53a5-404c-aaab-ab03c65ee748" />

  - Observa la función ofApp::draw(). ¿Qué operación realiza sobre el vector compartido?

    - <img width="599" height="206" alt="image" src="https://github.com/user-attachments/assets/12b8f7e4-4352-4367-8777-a48f2cb77ba3" />
    - <img width="395" height="217" alt="image" src="https://github.com/user-attachments/assets/805c3f0c-b306-420e-bc1d-4cc621c7e4a1" />

  - Observa Flock::addBoid() y ofApp::mouseDragged(). ¿Qué operación realizan?

    - <img width="261" height="85" alt="image" src="https://github.com/user-attachments/assets/98427eca-8571-4175-ab05-1c3056d7a8f2" />
    - <img width="618" height="95" alt="image" src="https://github.com/user-attachments/assets/20355111-fd47-4b8b-b6f3-da2b76d42795" />

    ni idea como funciona ese código pero ahí explica que mete el nuevo elemento al final del todo.

- **3.) Describe un escenario específico y concreto donde la falta de sincronización podría causar un problema. Por ejemplo:

> “El Hilo X está recorriendo el vector para calcular la separación (leyendo posiciones). Al mismo tiempo, el Hilo Y (llamado desde mouseDragged) intenta añadir un nuevo boid al final del vector. ¿Qué podría pasarle al iterador del Hilo X o al tamaño del vector que está usando?”

  - Pues desde un principio me pareció raro los llamados de update y draw, en update se están modificando la velocidad y la posición pero en draw se está leyendo la posición, lo que podría dar a lugar a una leve desincronización, aunque igual creería que no sería la gran cosa.

- **4.) Localiza todas las llamadas a lock() y unlock() dentro de la clase Flock (o donde se acceda al vector compartido).**

  - <img width="600" height="546" alt="image" src="https://github.com/user-attachments/assets/742b2175-ec0a-49cb-9f18-d2e983c236b1" />
 
> Justificación: para uno de los escenarios problemáticos que describiste arriba, explica cómo las llamadas a lock()/unlock() en las secciones de código relevantes evitan que ocurra ese problema específico.

  - Pues evitan que draw lea la posición cuando se está actualizando, de esa forma el dibujo en la pantalla y su posición real son las mismas.   

- **5.) Aunque los locks aseguran la correctitud, ¿Puedes intuir por qué tener muchos hilos esperando para adquirir un lock sobre el mismo vector (alta contención) podría limitar el beneficio de rendimiento del paralelismo en este caso? Justifica tu respuesta.**

  - Pues pasa que los hilos se quedan esperando a leer el vector, lo que si o si hace que el programa sea lento.

___

¿Qué pasaría si tuviéramos varios hilos que calculan el movimiento de los boids? ¿Cómo podrías implementar esto? ¿Qué problemas crees que podrían surgir? ¿Cómo podrías solucionarlos?

  - Pues supongo que se podrían hacer varios vectores de boids y asignarle a cada uno un hilo. Un problema grande de este código creo que es que para definir su comportamiento tiene en cuenta TODOS los boids, cuando solo debe tener en cuenta los que están cerca. Mi solución no funcionaría precisamente por eso, por que debe tener en cuenta la posición de todos. Lo otro que creo que sería útil sería que cada hilo se encargara como de una porción del espacio, así solo calcula los boids que estén ese lugar y ya.
  - De todas formas digamos hay un boid just afuera de ese espacio y uno adentro necesita modificar su posición, igual ahí se podría dar una lectura incorrecta del error.
  - No tengo ninguna solución, cualquier cosa creo que si se va a actualizar la posición de un boid no basta con solo ese espacio en el que está sino los que tenga alrededor, pero no sé hasta que punto eso sea más complejo.

__

# APPLY

## Actividad 5

cogí el código que no era y lo hice en el secuencial

<img width="237" height="231" alt="image" src="https://github.com/user-attachments/assets/e86b597c-d766-430d-a457-12fde0b616fd" />

es un poco lento pero se ve bonito, igual el tiempo de calculo está siempre en 0.2 y 0.1 segundos.

- Pega la parte clave de tu función modificada que calcula el píxel para el conjunto de Julia. Recuerda utilizar un bloque cpp.

  - <img width="480" height="216" alt="image" src="https://github.com/user-attachments/assets/d5d6bc33-29c3-4d0e-899f-241ccac1206e" />

- Muestra cómo mapeaste la posición del mouse a la constante k.

  - <img width="418" height="170" alt="image" src="https://github.com/user-attachments/assets/5a7c5e32-2462-47bb-9930-f662f2b5ac52" />


- Describe brevemente cómo reutilizaste la estructura de hilos de la versión Mandelbrot. ¿Tuviste que cambiar mucho esa parte?

  - No la tuve que cambiar en lo absoluto, no sé si eso sea bueno o malo, lo cierto es que no más llamé startCalculation() como hacian los otros dos triggers y esperaba que eso fuera suficiente.

- ¿Cómo te aseguraste de que la imagen se recalculara cuando el mouse se movía?

  - <img width="456" height="185" alt="image" src="https://github.com/user-attachments/assets/69c0f0b3-0b5a-4d33-bc27-da5efc5cc169" />

- Incluye al menos dos capturas de pantalla que muestren diferentes fractales de Julia generados al mover el mouse en tu aplicación.

  - Iba a buscar uno bien bacano pa poner pero vi esto entonces voy a intentar que se vea así, que genial.
  - <img width="803" height="672" alt="image" src="https://github.com/user-attachments/assets/a3996f80-7a19-440a-9827-e7291238e37d" />

  - <img width="1016" height="760" alt="image" src="https://github.com/user-attachments/assets/91b268bd-2266-409a-b1d3-c347f2e07567" />

  - <img width="553" height="261" alt="image" src="https://github.com/user-attachments/assets/eb682d36-0c33-4d4c-bf57-414ee957f861" />

  Entonces para z^4 sería lo siguiente: z = x + iy, entonces z^4 = (x + iy)^4 que es lo mismo que (x + iy)^2 * (x + iy)^2 que es como lo teniamos al principio y eso al final queda que x^4 + 4(x^3)yi + 6(x^2)(y^2 * i^2) + 4x(y^3* i^3) + (y^4* i^4) y ya para encontrar la parte real sería entonces volver a organizarlo de la forma a + bi y quedaría así: (x^4 - 6+x^2+y^2 + y^4) + i(-4x^3y + 4xy^3) y se supone que si pongo esos dos terminos como zx y zy quedaría bonito.

  - <img width="1020" height="767" alt="image" src="https://github.com/user-attachments/assets/b00da6ea-0084-423f-a027-3fb914a2cdcd" />
  ESOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

  - <img width="1006" height="734" alt="image" src="https://github.com/user-attachments/assets/728e2c7a-d6d0-436a-b74f-60aa03f5ab31" />

  - <img width="954" height="751" alt="image" src="https://github.com/user-attachments/assets/6ec4e708-793d-4985-83b4-608994aebbf6" />

- ¿Encontraste algún desafío particular al implementar la interacción o modificar el cálculo?

  - No realmente, es bastante intuitiva la implementación una vez se entiende la lógica detrás de como se calcula y se dibuja, en cuanto a lo del mouse me hubiera quedado un rato ahí pero el profe ya había explicado algo similar en físicos interactivos entonces tampoco fue un problema. 

