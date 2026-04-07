Arquitectura de Computadores — Unidad 3

Post-Contenido 2 — DEBUG: Ejecución Paso a Paso y Bucles

Descripción del Laboratorio

En este laboratorio se utilizó el depurador DEBUG para ensamblar programas directamente en memoria y ejecutarlos paso a paso mediante el comando T. Se analizaron los cambios en los registros y banderas después de cada instrucción.

Se desarrollaron dos programas:

Programa de suma con traza completa

Programa con bucle usando la instrucción LOOP

Además, se realizó el análisis del código máquina mediante el comando D.

Entorno de Trabajo

-DOSBox 0.74-3

-DEBUG

-Windows

-GitHub para documentación

Checkpoint 1 — Programa de Suma con Traza

Programa ensamblado:

MOV AX, 000A

MOV BX, 0005

MOV CX, 0003

ADD AX, BX

ADD AX, CX

INT 20

Observaciones:

AX se inicializa con 10 decimal (000A)

BX contiene 5 decimal

CX contiene 3 decimal

AX se incrementa en cada instrucción ADD

Resultado final AX = 0012 (18 decimal)

Captura:

capturas/CP1_traza_suma.png

Checkpoint 2 — Programa con Bucle LOOP

Programa ensamblado:

MOV AX, 0000

MOV CX, 0004

ADD AX, 0002

LOOP 0106

INT 20

Observaciones:

CX actúa como contador del bucle

LOOP decrementa CX automáticamente

Mientras CX ≠ 0 el programa regresa a la instrucción ADD

Se realizan 4 iteraciones

Resultado final AX = 0008 (8 decimal)

Captura:

capturas/CP2_traza_loop.png

Checkpoint 3 — Análisis del Código Máquina

Se utilizó el comando:

D CS:100 L0C

Salida esperada:

B8 00 00 B9 04 00 05 02 00 E2 FB CD 20

Interpretación:

Bytes	 |   Instrucción

B8 00 00 |	MOV AX,0000

B9 04 00 | MOV CX,0004

05 02 00 |	ADD AX,0002

E2 FB |	LOOP 0106

CD 20 |	INT 20

Análisis:

Cada instrucción ocupa diferente cantidad de bytes:

MOV AX, imm16 -> 3 bytes

MOV CX, imm16 -> 3 bytes

ADD AX, imm16 -> 3 bytes

LOOP -> 2 bytes

INT 20 -> 2 bytes

Esto demuestra cómo el procesador interpreta las instrucciones a partir del código máquina almacenado en memoria.

Conclusiones

Este laboratorio permitió comprender la ejecución paso a paso de instrucciones en el procesador mediante DEBUG. Se observó cómo los registros cambian después de cada instrucción y cómo la instrucción LOOP permite implementar bucles eficientes usando el registro CX.

Además, se analizó la representación del código ensamblador en código máquina, lo cual ayuda a comprender el funcionamiento interno del procesador x86.
