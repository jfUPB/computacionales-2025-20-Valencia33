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

## Actividad 02

### Orientación y primer vistazo al entorno gráfico

**¿Cómo se crean un proyecto openGL en Windows?**

**RESUMEN**

Basicamente, para crear un proyecto de estos se deben enlazar un par de bibliotecas, que van a funcionar tanto durante la compilación como la ejecución, esas bibliotecas son GLFW, opengl32, GLAD y GLM, cada una cumple una función distinta.

- GLFW es la que se encarga de crear la ventana y tales, tal y como lo haciamos en of.
- opengl32 es una biblioteca que es como nativa de windows y tiene como las funciones más básicas de opengl.
- GLAD este lo que hace es que añade incluso mas cositas de opengl y las corre en el driver.
- GLM se encarga de meter funciones matematicas que sirven para animaciones y tales, me lo imagino como todas esas funciones MathF de c#.

