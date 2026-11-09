Laboratorio SPIM — Compiladores

Programas en MIPS para ejecutar y depurar en QtSpim.

Archivo	Qué hace
hello.asm	Hello World
suma.asm	Código propio: suma de 1 a 5 con un ciclo, imprime Suma 1..5 = 15
Cómo correrlo
Instalar QtSpim desde https://sourceforge.net/projects/spimsimulator/files/
Abrir QtSpim → File > Reinitialize and Load File → elegir el .asm.
Ejecutar paso a paso con el botón Single Step (F10) y ver el panel Int Regs a la izquierda. El registro que cambia se resalta.
Run (F5) lo ejecuta completo; la salida sale en la ventana Console.

Desde terminal: spim -file hello.asm


Link al video https://youtu.be/sC61j4FV_Ts
