# Bitácora de aprendizaje de la unidad 7

> Navegar un proyecto OpenGL básico: entenderás la estructura y el ciclo de vida de una aplicación gráfica simple.
> Identificar el rol de los Shaders: modificarás vertex y fragment shaders básicos (GLSL) y entenderás su impacto.
> Comprender el flujo de datos: analizarás cómo los datos de vértices (VBOs) se conectan a los shaders a través de la configuración de estado (VAOs).
> Usar Uniforms: pasarás datos dinámicos desde C++ a tus shaders.
> Aplicar conocimientos: reforzarás tu aprendizaje mediante la solución de un problema sencillo.


## Actividad 1

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

## Actividad 2

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

  - Ese es el programa que indica como se van a dibujar los vertices, es importante por que en últimas es lo que dicta la apariencia al final. 

- Trata de revisar el código setupTriangle(), intuitivamente ¿Qué crees que hace? ¿Qué crees que es el VAO y el VBO?

  - leyendo un blogsito ya me hice spoiler de lo que era vertex array object y un vertex buffer object, entonces juzgando por sus nombres diría que un vao guarda los vertices, y el vbo guarda como la apariencia de estos vertices que guarda. 

- En el ciclo principal (game loop) de OpenGL, notaste que en cada frame (cuadro) le decimos a openGL que use el shader program y el VAO. Si le indicas esto antes del game loop ¿Será necesario seguirlo haciendo en cada loop? Si no es necesario ¿En qué casos crees que esto puede ser útil?

  -  Yo diría que no es necesario, siento que tendría sus complicaciones si no se hace, en el sentido en el que solo utilizaría la versión del programa que declaramos al principio, entonces diría que es util en casos donde sabemos que vamos trabajar siempre con la misma información.

- Finalmente, recuerda lo que hace glfwSwapBuffers(mainWindow); ¿Por qué crees que es importante? ¿Qué pasaría si no lo llamas? ¿Cómo explicas lo que pasa si no lo llamas? (experimenta)

  - Es importante por que de esa forma se muestra lo que se ha dibujado cada frame, si no lo llamo, entonces no habrá dibujado nada y no se verá nada. 
 
## Actividad 4

### ¿Cuál es la diferencia entre una CPU y una GPU?

La diferencia es que la CPU realiza todas las actividades para renderizar paso a paso. A diferencia de la CPU, la GPU dibuja todo antes de mostrarlo, lo que en últimas es más rápido y organizado.

- 1.) ¿Cuáles son los tres pasos claves del pipeline de OpenGL? Explica en tus propias palabras cuál es el objetivo de cada paso.

  - vertex shading se encarga de coger la posición 3d de TODOS los vertices que puede ver la cámara y proyectarlos en un plano 2d (cameraview), la rasterización es la parte del proceso donde se define que pixeles de la pantalla le corresponden a que triangulo, aplicando las texturas, por último en fragment shading lo que se hace es que se aplican materiales y luces, es decir calcula los rayos de luz y sombras.

- 2.) La gran novedad que introduce OpenGL moderno es el pipeline programable. ¿Qué significa esto? ¿Qué diferencia hay entre el pipeline fijo y el programable? ¿Qué ventajas le ves a esto? y si el pipeline es programable, ¿Qué tengo que programar?

  - Esto significa que la apariencia de los vcertices cuando se dibujam ya no se hace con funciones preestablecidad, sino que se necesitan shaders para hacer esto, lo que permite mucha más flexibilidad y control sobre el resultado final.

- 3.) Si fueras a describir el proceso de rasterización ¿Qué dirías?

  - Diría que es una especie de traducción, de coordenadas x,y y z en un espacio 3D a pixeles en la pantalla 2D

- 4.) ¿Qué son los fragmentos? ¿Es lo mismo un fragmento que un pixel? ¿Por qué?

  - no no, no son lo mismo, un pixel es el resultado final, pero los fragmentos son como esas porciones en la pantalla a lo que se le van aplicando cosas

- 5.) Explica qué problema resuelve el Z-buffer y ¿Qué es el depth test?

  - el z-buffer lo que hace es que decide QUE se renderiza primer, es genial por que de esa forma se evita que se dibujen cosas que no se van a haber y que clipeen entre ellas.

- 6.) ¿Por qué se presenta el problema de la aliasing? ¿Qué es el anti-aliasing?

  - como me lo imagino es que se intenta dibujar una linea que está compuesto por puntos infinitos encima de una cuadricula, lo que sucede es que el cambio en x y y en la cuadricula es muy muy obvio, entonces se ve raro, se ve pixelado. el antialising lo que hace es que "difumina" esos bordes de tal forma que no se vea pixelado sino un poco más suavizado.

- 7.) ¿Qué relación hay entre la iluminación y el fragment shader? Siempre es necesario tener en cuenta la iluminación en un fragment shader? o puedo hacer un fragment shader sin iluminación? Explica que implicaciones tiene esto.

  - la relación que existe es que el fragment sahder toma en consideración la iluminación, la orientación de las cosas, su material y la cámara antes de dibujar los pixeles finales. Y no, no creo que sea necesario más que todo por que lo he visto en blender pero no sé si ese caso aplique.

- 8.) ¿Qué implica para la GPU que una aplicación tenga múltiples fuentes de iluminación?

  -  pues me imagino que mucho más trabajo, en el sentido en el que tendrá que calcular y recorrer el proceso de luz, orientación, material, cámara por cada fuente de luz.

**Escribe un resumen en tus propias palabras de lo que se necesita para dibujar un triángulo en OpenGL.**

BUneo lo primero que se necesita para dibujar un triangulo es la información de sus vertices, de esta forma se puede crear unos vertices que hay que enviarlos a un vbo, que como dije antes es lo que contiene las caracteristicas de cada vertices, para estoy igual hay que decirle varias cosas, primero, a que tipo de buffer, que tamaño tiene la info que le vamos a enviar, la info y si es constante o dinámica. Por último toca habilitar el atributo de vertice, este cosito lo que hace es que coge los vertices que le pasemos y los convierte como a sets de información ligados a un ID, esto es para que el shader los pueda manipular despues, ya posterior a esto se le aplican los shaders y tales pero eso lo digo en la siguiente pregunta.

**Escribe un resumen en tus propias palabras de lo que necesitas para poder usar un shader en OpenGL.**

Para poder usarlos hay que crear un objeto que tiene un ID, este objeto sera el programa de los shaders  la cosa es que aún no está activo, se debe de activar, esto se hace indicandole a NUESTRO programa que programa de shader debe utilizar para dibujar cada cosa, entonces ya cuando se llama un método para dibujar alguna cosita el programa ya sabe cual es su ruta por la GPU.

**Implementa el código anterior en tu máquina y captura pantalla del resultado. Pero antes de hacerlo trata de predecir qué va a pasar.**

Pues algo es seguro y es que se van a dibujar 3 triangulos, cada uno con un shader diferente, no tengo NI IDEA que hace cada shader, creo que no más lo mueve pq en niguna parte mueve lo de frag color pero sinceramente no sé.

ni idea si este es el output:

<img width="409" height="442" alt="image" src="https://github.com/user-attachments/assets/767ba5dc-00fa-4842-914c-f0e674ae0241" />

## Actividad 5

- 1.) Incluye una captura de pantalla del triángulo interactivo funcionando en tu máquina.

  - <img width="803" height="606" alt="image" src="https://github.com/user-attachments/assets/8e86acd7-3c7f-44c9-8ec2-4071f8a24473" />

  - <img width="799" height="627" alt="image" src="https://github.com/user-attachments/assets/d76e6d5f-9d03-4ec4-b769-ed94749198de" />

  - <img width="799" height="599" alt="image" src="https://github.com/user-attachments/assets/4dc2430a-ecc5-44b2-b0d1-3945d0e7564c" />

  - <img width="794" height="608" alt="image" src="https://github.com/user-attachments/assets/cd456947-5423-41dd-95cd-c797c74e448f" />

- 2.) Explica el proceso de normalización de las coordenadas del mouse y cómo se relaciona con el sistema de coordenadas de OpenGL.

  - <img width="483" height="128" alt="image" src="https://github.com/user-attachments/assets/1e118f98-3e61-43cd-95fa-114d2f3a7e7e" />

  - Lo que hace es que coge la posición del mouse dentro de la pantalla y la divide por width o height, dependeiendo del caso, esto lo que hace es que normaliza x para que solo pueda tomar un valor de 0 a 1.
  - se relaciona con el sistema de coordenadas de openGL por que este es un sist coordenado normalizado.

- 3.) Explica el proceso de normalización a coordenadas de dispositivo (NDC) y cómo se relaciona con el sistema de coordenadas de OpenGL.

  - lo que pasa es que openGL trabaja con un espacio q va de -1 a 1, por esto para las coordenadas de los vertices del triangulo se debe aplicar una transformación adicional que es x/y = x/y * 2 + 1, de esa forma se convierten los vertices a ndc.

## Actividad 6

- **1.) Describe brevemente los cambios que realizaste en el código C++ (dónde obtienes el tiempo, cómo y dónde actualizas el uniform).**

  - el tiempo lo obtengo con la función que el profe mencionó y lo actualizo en cada iteración del loop principal. ya en el shader lo que hago es que utilizo ese uniform en cada parámetro que recibe el vec4 de FragColor.

  - exactamente los cambios que hice fueron:

    - <img width="462" height="82" alt="image" src="https://github.com/user-attachments/assets/68600f25-0952-4850-8aa2-b482212bf063" />

    - <img width="536" height="141" alt="image" src="https://github.com/user-attachments/assets/f510b11a-9d59-4a4c-bfc2-eb382c213967" />

    - <img width="547" height="421" alt="image" src="https://github.com/user-attachments/assets/3d2bf02f-b90c-4c32-b19b-8cc05e97fecd" />

    - Si quería que se moviera con el mouse pero no que cogiera el color de ahí, entonces no más fue reemplazarlo.

- **2.) Pega el código modificado de tu fragment shader.**

```c++
#include <iostream>
#include <glad/glad.h>
#include <GLFW/glfw3.h>

void framebuffer_size_callback(GLFWwindow* window, int width, int height) {
    glViewport(0, 0, width, height);
}

void processInput(GLFWwindow* window) {
    if (glfwGetKey(window, GLFW_KEY_ESCAPE) == GLFW_PRESS)
        glfwSetWindowShouldClose(window, true);
}

const unsigned int SCR_WIDTH = 800;
const unsigned int SCR_HEIGHT = 600;

const char* vertexShaderSrc = R"glsl(
    #version 460 core
    layout(location = 0) in vec3 aPos;
    uniform vec2 offset;

    void main() {
        vec3 newPos = aPos;
        newPos.x += offset.x;
        newPos.y += offset.y;
        gl_Position = vec4(newPos, 1.0);
    }
)glsl";

const char* fragmentShaderSrc = R"glsl(
    #version 460 core
    out vec4 FragColor;
    uniform float timeValue;

    void main() {
        FragColor = vec4(cos(timeValue),sin(timeValue),cos(timeValue),1.0);
    }
)glsl";

unsigned int VAO, VBO;
unsigned int shaderProg;

unsigned int buildShaderProgram(const char* vSrc, const char* fSrc) {
    int success;
    char log[512];

    unsigned int vs = glCreateShader(GL_VERTEX_SHADER);
    glShaderSource(vs, 1, &vSrc, nullptr);
    glCompileShader(vs);
    glGetShaderiv(vs, GL_COMPILE_STATUS, &success);
    if (!success) {
        glGetShaderInfoLog(vs, 512, nullptr, log);
        std::cerr << "ERROR VERTEX SHADER:\n" << log << "\n";
    }

    unsigned int fs = glCreateShader(GL_FRAGMENT_SHADER);
    glShaderSource(fs, 1, &fSrc, nullptr);
    glCompileShader(fs);
    glGetShaderiv(fs, GL_COMPILE_STATUS, &success);
    if (!success) {
        glGetShaderInfoLog(fs, 512, nullptr, log);
        std::cerr << "ERROR FRAGMENT SHADER:\n" << log << "\n";
    }

    unsigned int prog = glCreateProgram();
    glAttachShader(prog, vs);
    glAttachShader(prog, fs);
    glLinkProgram(prog);
    glGetProgramiv(prog, GL_LINK_STATUS, &success);
    if (!success) {
        glGetProgramInfoLog(prog, 512, nullptr, log);
        std::cerr << "ERROR LINKING PROGRAM:\n" << log << "\n";
    }

    glDeleteShader(vs);
    glDeleteShader(fs);
    return prog;
}

void setupTriangle() {
    float vertices[] = {
        -0.5f, -0.5f, 0.0f,
         0.5f, -0.5f, 0.0f,
         0.0f,  0.5f, 0.0f
    };

    glGenVertexArrays(1, &VAO);
    glGenBuffers(1, &VBO);

    glBindVertexArray(VAO);
    glBindBuffer(GL_ARRAY_BUFFER, VBO);
    glBufferData(GL_ARRAY_BUFFER, sizeof(vertices), vertices, GL_STATIC_DRAW);
    glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 3 * sizeof(float), (void*)0);
    glEnableVertexAttribArray(0);
    glBindVertexArray(0);
}

int main() {
    if (!glfwInit()) {
        std::cerr << "Fallo al inicializar GLFW\n";
        return -1;
    }
    glfwWindowHint(GLFW_CONTEXT_VERSION_MAJOR, 4);
    glfwWindowHint(GLFW_CONTEXT_VERSION_MINOR, 6);
    glfwWindowHint(GLFW_OPENGL_PROFILE, GLFW_OPENGL_CORE_PROFILE);

    GLFWwindow* mainWindow = glfwCreateWindow(SCR_WIDTH, SCR_HEIGHT, "Ventana", nullptr, nullptr);
    if (!mainWindow) {
        std::cerr << "Error creando ventana\n";
        glfwTerminate();
        return -1;
    }

    glfwMakeContextCurrent(mainWindow);
    glfwSetFramebufferSizeCallback(mainWindow, framebuffer_size_callback);

    if (!gladLoadGLLoader((GLADloadproc)glfwGetProcAddress)) {
        std::cerr << "Fallo al cargar GLAD\n";
        return -1;
    }

    glfwSwapInterval(1);

    shaderProg = buildShaderProgram(vertexShaderSrc, fragmentShaderSrc);
    setupTriangle();

    glUseProgram(shaderProg);
    int offsetLocation = glGetUniformLocation(shaderProg, "offset");
    int timeLocation = glGetUniformLocation(shaderProg, "timeValue");
    int colorLocation = glGetUniformLocation(shaderProg, "ourColor");

    while (!glfwWindowShouldClose(mainWindow)) {
        glfwPollEvents();
        processInput(mainWindow);

        glClearColor(0.2f, 0.3f, 0.3f, 1.0f);
        glClear(GL_COLOR_BUFFER_BIT);

        double xpos, ypos;
        glfwGetCursorPos(mainWindow, &xpos, &ypos);

        float x = static_cast<float>(xpos) / static_cast<float>(SCR_WIDTH);
        if (x < 0) x = 0;
        if (x > 1) x = 1;

        float y = static_cast<float>(ypos) / static_cast<float>(SCR_HEIGHT);
        if (y < 0) y = 0;
        if (y > 1) y = 1;

        double timeValue = glfwGetTime();
        glUniform1f(timeLocation, static_cast<float>(timeValue));
        glUniform2f(offsetLocation, x * 2.0f - 1.0f, 1.0f - y * 2.0f);

        glBindVertexArray(VAO);
        glDrawArrays(GL_TRIANGLES, 0, 3);

        glfwSwapBuffers(mainWindow);
    }

    glfwMakeContextCurrent(mainWindow);
    glDeleteVertexArrays(1, &VAO);
    glDeleteBuffers(1, &VBO);
    glDeleteProgram(shaderProg);

    glfwDestroyWindow(mainWindow);
    glfwTerminate();
    return 0;
}
```

- **3.) Explica cómo usaste la función de tiempo (sin, cos, u otra) para lograr el efecto de cambio de color cíclico. ¿Qué rango de valores produce tu cálculo y cómo afecta eso al color final?**

  - en este punto si creo que fuí bastante simple, no más de los 3 parámetros que recibe como rgb pasé un coseno y seno que tenían como ángulo el tiempo, entonces realmente no hace gran cosa más allá de ir bastante lento en el cambio de colores, para arreglar esto podría multiplicar el cos y sen pero ya pegué el código entonces no lo pienso hacer.
 
  - <img width="615" height="71" alt="image" src="https://github.com/user-attachments/assets/411a3087-6d3c-4c3d-b4ee-a37a7ef4a133" />

  - lo que si vi que pasaba que me parecio muy charro es que como no hay ningún tipo de offset entonces los colores están limitados a verde y morado, para arreglar esto se le podría sumar, que este si lo voy a hacer para las fotitos. 

- **4.) Incluye una captura de pantalla o UN ENLACE a un video mostrando el resultado del triángulo con color cambiante.**

  - <img width="792" height="589" alt="image" src="https://github.com/user-attachments/assets/5a7d3cd2-c292-4b27-bb24-0363c42aa6e9" />

  - <img width="793" height="594" alt="image" src="https://github.com/user-attachments/assets/8c1a6cbd-8692-42ad-933c-78ddf9e59a1a" />

  - <img width="795" height="586" alt="image" src="https://github.com/user-attachments/assets/cf9b3050-439a-4571-ab24-66d7aa90861b" />

  - <img width="791" height="582" alt="image" src="https://github.com/user-attachments/assets/4ad3d45f-e7d5-4df4-9860-d92958fe8cd1" />

  - <img width="789" height="588" alt="image" src="https://github.com/user-attachments/assets/890e1825-3961-4050-9de8-8a50bbbcdce4" />

- **5.)Reflexión: ¿Qué otros efectos visuales simples podrías lograr usando el tiempo como uniform? Piensa en la posición, el tamaño o la rotación (aunque no hemos visto rotaciones formalmente, ¡intuitivamente podrías intentarlo!). Anota al menos una idea.**

  - LA POSICIÓN DE UN VERTICE, no tengo ni idea de si se podria, o tendría que pensar como tal en el fragmento, pero pienso que algo así se vería divertido y en base a la posición que tenga el vertice asignar un color.  

# EVIDENCIAS

## MI NOTA: 5

- **Actividad 1**
	- Realicé todo lo que proponía la actividad.
 	- [EVIDENCIA](#actividad-1)
- **Actividad 2**
	- Realicé todo lo que proponía la unidad, incluso aquellas preguntas que no eran obligatorias.
 	- [EVIDENCIA](#actividad-2)
- **Actividad 3**
	- Realicé todo lo que proponía la unidad, incluso aquellas preguntas que no eran obligatorias.
	- [EVIDENCIA](#actividad-3)
- **Actividad 4**
	- Realicé todo lo que proponía la unidad, incluso aquellas preguntas que no eran obligatorias.
	- [EVIDENCIA](#actividad-4)
- **Actividad 5**
	- Realicé todo lo que proponía la unidad, incluso aquellas preguntas que no eran obligatorias.
	- [EVIDENCIA](#actividad-5)
- **Actividad 6**
	- Realicé todo lo que proponía la unidad, incluso aquellas preguntas que no eran obligatorias.
	- [EVIDENCIA](#actividad-6)
