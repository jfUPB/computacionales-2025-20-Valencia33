# Bitácora de aprendizaje de la unidad 6

## Actividad 1

- **1.) ¿Cómo puedes interactuar con la aplicación?**

  - Se puede interactuar por medio de cuatro inputs, s, a, r y n. En ese orden, el comportamiento de cada una sobre las particulas es: Stop congela la posición de las particulas hasta que se presione de nuevo, Attract interpola la posición de las particulas al del mouse, Reppel aleja las particulas del mouse y Normal que se encarga de que su comportamiento sea normal.

- **2.) ¿Observas los diferentes tipos de “partículas”? ¿Se comportan todas igual inicialmente?**

  - A simple vista parece que todas se comportan de igual forma, lo que sucede es que su velocidad color y tamaño es diferente, pero esto solo desde el estado inicial es a única diferencia notable. En total cuento 3, una bolita verde que es muy rápida y pequeña, otra que es grande y azul y por último una verde, tengo la sospecha de que estas dos últimas tienen la misma velocidad.
 
- **3.) Toma algunas capturas de pantalla de la aplicación en diferentes momentos**

**INICIAL**
<img width="1014" height="751" alt="image" src="https://github.com/user-attachments/assets/61ae4c93-0681-4cd1-82dd-be0985f83add" />

**ATRACT**
<img width="1015" height="762" alt="image" src="https://github.com/user-attachments/assets/d2e7fce0-c84a-4dbd-a4f3-f1ac249d79ff" />

**REPPEL**
<img width="1019" height="768" alt="image" src="https://github.com/user-attachments/assets/8c780e52-2bd5-4118-b6e5-aedd84f2d817" />

**STOP** (están quietas)
<img width="1018" height="764" alt="image" src="https://github.com/user-attachments/assets/69fc179a-28e3-4453-b18f-7949c179787e" />

**NORMAL**
<img width="1018" height="768" alt="image" src="https://github.com/user-attachments/assets/716c9e35-f7fa-4861-b5bf-6d17a85f262b" />

- **4.) ¿Qué crees que está pasando “detrás de cámaras” cuando presionas las teclas?**

  - Pues el profe en este momento me está explicando justo lo que pasa detrás de camaras, pero me voy a hacer el bobo y voy a decir lo que diría si no supiera. Diría que cada frame se está actualizando la posición de cada particula con respecto a una variable que corresponde al input, y esta es la que define el como cambia en el tiempo la velocidad y posición de las particulas.

