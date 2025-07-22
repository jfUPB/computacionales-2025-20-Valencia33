# Unidad 1

## 🛠 Fase: Apply

♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️♾️

### 🐟 Actividad 3 🐟 

#### __Control de flujo con saltos___

Escribe un programa que compare el valor almacenado en la dirección de memoria 5 con el valor 10. Si el valor es menor que 10, guarda el valor 1 en la dirección 7. Si el valor es mayor o igual a 10, guarda el valor 0 en la dirección 7.

Hice dos por que me pareció que era muy simple y el loop muy rápido, entonces la segunda versión toma un valor del teclado y lo compara con 100 y corre el mismo proceso:

```asm
(INICIO)
@KBD
D=M
@100
D=A-D
@MENOR
D;JGE //(D>=0)
@MAYORIGUAL
0;JMP

(MAYORIGUAL)
@7
M=0
@INICIO
0;JMP

(MENOR)
@7
M=1
@INICIO
0;JMP
```
El del enunciado:

```asm
(INICIO)
@KBD
D=M
@5
M=D
D=A
@10
D=A-D
@MENOR
D;JGE //(D>=0)
@MAYORIGUAL
0;JMP

(MAYORIGUAL)
@7
M=0
@INICIO
0;JMP

(MENOR)
@7
M=1
@INICIO
0;JMP
```
