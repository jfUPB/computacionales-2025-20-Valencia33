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



