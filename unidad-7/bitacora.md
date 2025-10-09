# Bitácora de aprendizaje de la unidad 7

> Navegar un proyecto OpenGL básico: entenderás la estructura y el ciclo de vida de una aplicación gráfica simple.
> Identificar el rol de los Shaders: modificarás vertex y fragment shaders básicos (GLSL) y entenderás su impacto.
> Comprender el flujo de datos: analizarás cómo los datos de vértices (VBOs) se conectan a los shaders a través de la configuración de estado (VAOs).
> Usar Uniforms: pasarás datos dinámicos desde C++ a tus shaders.
> Aplicar conocimientos: reforzarás tu aprendizaje mediante la solución de un problema sencillo.


## Actividad 01

**Ejemplo simple de un triángulo en OpenGL:**

- **Incluye una captura de pantalla del ejemplo funcionando en tu máquina.**

  - <img width="1476" height="1078" alt="image" src="https://github.com/user-attachments/assets/3bb4e6a4-88ba-4521-b71e-d666c575ba9f" />

- **Observa el proyecto, trata de entenderlo, pero ten presente que lo analizaremos más adelante.**

  - Hay conceptos con los que soy familiar en el código, por ejemplo la detección de inputs, o la creación de la ventana. Sin embargo hay cosas que nada que ver y es realmente todo lo que toma lugar en la GPU, me puedo imaginar que es lo que hacen algunas cosas.

- **¿Qué preguntas te surgen al ver el código?. Anota al menos tres preguntas que te gustaría investigar más adelante (no te preocupes que la idea de esta unidad es que las resuelvas).**

  - ¿Que función cumple el Vsync? partiendo de que es un concepto familiar en los videojuegos.
  - ¿Como se leen o utilizan las extensiones de OpenGL?
  - ¿Que es y para que sirve GLFW?
  - ¿Que es el framebuffer?

## Actividad 02

### Orientación y primer vistazo al entorno gráfico

**¿Cómo se crean un proyecto openGL en Windows?**

**RESUMEN**

Basicamente, para crear un proyecto de estos se deben enlazar un par de bibliotecas, que van a funcionar tanto durante la compilación como la ejecución, esas bibliotecas son GLFW, opengl32, GLAD y GLM, cada una cumple una función distinta.

- GLFW es la que se encarga de crear la ventana y tales, tal y como lo haciamos en of.
- opengl32 es una biblioteca que es como nativa de windows y tiene como las funciones más básicas de opengl.
- GLAD este lo que hace es que añade incluso mas cositas de opengl y las corre en el driver.
- GLM se encarga de meter funciones matematicas que sirven para animaciones y tales, me lo imagino como todas esas funciones MathF de c#.

## Actividad 3

<img width="1003" height="337" alt="image" src="https://github.com/user-attachments/assets/8116960c-afd1-4d71-a058-dd0ca9ff3f0c" />

- **PREGUNTA 3:** ¿Que es y para que sirve GLFW?

  - GLFW es quella biblioteca que le da las herramientas para poder visualizar lo que hacemos en openGL.

- **PREGUNTA 4** ¿Que es el framebuffer?

  - acá es donde dibuja openGL, me lo imagino como un boceto o unas instrucciones que se le pasan a la GPU para que realmente pueda dibujar.

<img width="728" height="159" alt="image" src="https://github.com/user-attachments/assets/94e5abcd-7dd0-496f-a97f-a663098ee564" />

- glViewport(0, bufferHeight/2, bufferWidth/2, bufferHeight/2);

  - <img width="400" height="430" alt="image" src="https://github.com/user-attachments/assets/fda791e4-81f5-4fe5-ae65-5564901021f8" />

- glViewport(0, 0, bufferWidth, bufferHeight);

  - <img width="402" height="435" alt="image" src="https://github.com/user-attachments/assets/478c20f8-1266-43e3-b8db-2d90bd24334d" />
 
- **Cambia los valores de bufferWidth y bufferHeight: divide por 2, por 4, multiplica por 2, por 4, etc. ¿Qué pasa? ¿Qué observas? ¿Qué crees que está pasando?**

  - Lo que veo que está pasando es como si estuviera escalando el canva "real", en el sentido en el que cuando se divide por dos realmente lo que está pasando es que ahora solo va a dibujar en 1/4 del tamaño total, por lo que me imagino que si se multiplica por dos entonces haría que el triangulo fuera mucho más grande, 4 veces más grande.

  - <img width="406" height="433" alt="image" src="https://github.com/user-attachments/assets/12b06567-8798-4600-9c3d-ebaff4a3af21" />

- **En tu bitácora, escribe un resumen de lo que has aprendido hasta ahora y piensa en un experimento del tipo ¿Qué pasaría si?**
 
   - Hasta ahora ya en mi cabeza tengo una idea más completa de todo lo que conlleva y que trabajo realiza cada una de las partes. Ya entendí el como va el flujo de instrucciones, en un principio se utiliza GLFW para crear nuestro "canva" nos da las herramientas para poder dibujar en esa ventana, despues está openGL, que es el que da instrucciones y es el que le dice a la GPU que debe de hacer, para esto, le dibuja un boceto en el framebuffer y de esa forma ya la GPU puede aplicarle shaders y texturas y demás cosas y dibujarlo en nuestra pantalla.
 
- **EXPERIMENTO**

  - voy a hacer daños en esta parte del código, por que por lo que entiendo cada columna (o fila, la verdad ni idea) es un vertice del triangulo. Acá analizando creo que es las filas por que tienen un 3er parametro que me imaginó será la Z y no lo usan, lo voy a usar
  - <img width="618" height="272" alt="image" src="https://github.com/user-attachments/assets/2e7293e0-900f-480e-b785-200eb320d2f9" />

  - Dañé el puntero del shader, cambié los vertices, aprendía dibujar un rectangulo y le cambié el color, mi objetivo era medio aprender a hacer el triangulo RGB que hace toda la gente que quiere construir su propio unity. EL resultado despues de muchos errores fue esto:
  - <img width="406" height="441" alt="image" src="https://github.com/user-attachments/assets/a35ce9bf-a039-4809-8863-303b6f91ec04" />
  - Todo salió mal entonces te la quedo debiendo pal apply :(
 
  - Pero también me encontré esto:
  - <img width="670" height="501" alt="image" src="https://github.com/user-attachments/assets/85a2add0-b0d2-4708-a208-7cfbcceb1d61" />
  - será una herramienta para despues

- **¿Qué pasa si cambias el primer parámetro de glDrawArrays a GL_LINES? ¿Qué pasa si lo cambias a GL_POINTS? ¿Qué pasa si cambias el tercer parámetro a 2? ¿Qué pasa si lo cambias a 4?**

  - <img width="423" height="449" alt="image" src="https://github.com/user-attachments/assets/61dd985d-c399-4e28-8d83-50f031d7af0c" />

  - <img width="410" height="439" alt="image" src="https://github.com/user-attachments/assets/a1a1c8d5-3954-481b-9fa2-0205ac4a0bbf" />

___

- ¿Qué es el contexto OpenGL?

  - el contexto openGL es el espacio de trabajo en openGL, es decir, ahí están todas las herramientas, los shaders, las texturas y las instrucciones, tambien mencionaban algo de la versión pero la verdad no me acuerdo. 

- ¿Cuál es el rol de la biblioteca GLFW y qué ventaja tiene usarla?

  - GLFW aún no estoy muy seguro pero creo que es por que si funciona no debería notarlo, precisamente por que se encarga de facilitar y de ser una especie de "traducción", nos brinda la creación de contextos de openGL y demás herramientas que en últimas nos facilita el trabajo. 

- ¿Por qué crees que OpenGL necesita un contexto (recuerda la analogía del taller de arte)?

  - Por que necesita saber donde va a dibujar las cositas, yo me imagino un contexto de openGL es como una instancia, y esa instancia necesita una ventana para dibujar lo que contiene en ella. 

- ¿En últimas qué será el framebuffer y a qué te recuerda de las dos primeras unidades del curso?

  - el framebuffer es donde se dibuja, es donde openGL escribe instrucciones y donde la GPU ejecuta y dibuja, fisicamente es la memoria VRAM. Me recuerda a la primer y segunda unidad por que existe una especie de traducción a "bajo nivel" en nuestro caso es la interpretación que hace la GPU de las instrucciones que manda openGL. 

- ¿Qué relación entre en el viewport y el framebuffer?

  - la relación que tienen es que en ambos se dibuja, sin embargo tienen un proceso diferente, en el framebuffer se interpretan los vertices y los shaders y las texturas. Y el viewport es utilizado para ver ese framebuffer, en el viewport es donde en ultimas la GPU dibuja cuando aplica shaders. 

- ¿En todo la analizado hasta ahora qué rol juega los drivers de la GPU y la GPU misma?

  - ni idea la verdad, esperen busco. Ya listo, los drivers de la GPU tienen todas las funciones modernas de openGL mientras que la GPU se encarga de interpretar datos. 

- ¿Por qué crees que sea necesario activar el VSync? ¿Si no lo activas y la imagen es estática qué crees que pase, y si es dinámica?

  - Es necesario por que de esa forma no se generan frames mientras se refresca la pantalla, en una imagen estática, creo que nada, pero la verdad no estoy seguro de que pueda pasar entonces voy a hacer daños.
  - no pasó nada.

- En esta unidad estamos usando OpenGL moderno, pero ¿Qué es OpenGL Legacy? ¿Qué diferencias hay entre ambos?

  - Al parecer era el openGL que se utilizaba en equipos más viejos, aunque por lo que vi cuando busqué la principal diferencia es la facilidad que tiene openGL moderno de escribir e interpretar shaders, cosa que el otro también puede hacer pero le cuesta más 

- ¿Qué es el shader program? ¿Por qué es importante en OpenGL moderno?
- Trata de revisar el código setupTriangle(), intuitivamente ¿Qué crees que hace? ¿Qué crees que es el VAO y el VBO?
- En el ciclo principal (game loop) de OpenGL, notaste que en cada frame (cuadro) le decimos a openGL que use el shader program y el VAO. Si le indicas esto antes del game loop ¿Será necesario seguirlo haciendo en cada loop? Si no es necesario ¿En qué casos crees que esto puede ser útil?
- Finalmente, recuerda lo que hace glfwSwapBuffers(mainWindow); ¿Por qué crees que es importante? ¿Qué pasaría si no lo llamas? ¿Cómo explicas lo que pasa si no lo llamas? (experimenta)
 
 

