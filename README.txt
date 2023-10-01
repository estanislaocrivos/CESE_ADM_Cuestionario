Arquitectura de Microprocesadores 

CESE 2023_CO20

Cuestionario de la materia

1. A continuación se listan algunas características de los tres procesadores y sus principales diferencias:

Los procesadores Cortex M0 tienen un set de instrucciones Thumb reducido con respecto a los procesadores M3 y M4 (con repertorio completo). 

La arquitectura de los Cortex M0 es del tipo Von Neumann (bus de memoria de datos y de instrucciones único), mientras que la arquitectura de los Cortex M3 y M4 es del tipo Harvard (bus de memoria de datos y de instrucciones por separado) de 32 bits.

Los cortex M3 y M4 implementan un pipeline de 3 etapas (Fetch, Decode, Execute) que "paraleliza" la ejecución de instrucciones.

Los Cortex M0 suelen ser utilizados en aplicaciones de bajo costo que consuman pocos recursos.

Los Cortex M3 y M4 agregan varias funcionalidades con respecto al M0 como por ejemplo módulos de división por HW, o la posibilidad de operar multiplicaciones con resultados en 32 o 64 bits.

Los procesadores M4 suelen ser utilizados en aplicaciones como el procesamiento de señales digitales, donde se requiere operar grandes cantidades de datos a partir de una única instrucción (SIMD) haciendo uso de operaciones MAC (Multiply and Accumulate).

2. El set de instrucciones Thumb, al ser de 32 bits con respecto al set de ARM de 64 bits, permite que el código ocupe menos lugar en memoria. Este set se utiliza principalmente en aplicaciones en las que existe una restricción en el tamaño de la memoria y el ancho de banda del bus.

3. Las arquitecturas Load - Store son las arquitecturas que operan exclusivamente con datos que se encuentren en registros. Es decir que al traer un dato desde memoria lo almacenan de forma intermedia en un registro, luego las instrucciones operan entre datos de registros y luego almacenan el resultado en otro registro. Finalmente, se almacena el dato del registro en memoria a través de una instrucción dedicada.

4. Regiones de memoria principal: Estas regiones contienen la memoria principal del sistema, que se utiliza para almacenar el código, los datos y la pila.

Regiones de memoria periférica: Estas regiones contienen los registros y periféricos del procesador.

Regiones de memoria flash: Estas regiones contienen el código de arranque y la memoria flash para el almacenamiento de datos.

Regiones de memoria RAM: Estas regiones contienen la memoria RAM para el almacenamiento de datos.

5. Los shadowed pointers del PSP y MSP son punteros a la pila de los modos Thread y Handler, respectivamente. Se utilizan para mejorar el rendimiento de las aplicaciones al evitar que el procesador tenga que cargar la pila desde la memoria principal. Los shadowed pointers del PSP y MSP almacenan la pila en una memoria especial llamada Shadow Register File (SRF). El SRF es una memoria de acceso rápido que se utiliza para almacenar los registros más utilizados del procesador.

6. Los modos de privilegio y operación de los Cortex M son: Privileged Thread, Unprivileged Thread y Privileged Handler. 

Cuando se programa un microcontrolador de la forma bare - metal (programación tradicional haciendo uso del bucle while(1) para ejecutar las distintas instrucciones) el modo de operación del uC es el de Privileged Thread, en el cual uno tiene acceso irrestricto a todos los recursos del uC, a todo el mapa de memoria, etcétera. Depende del programador hacer buen uso del uC. En este modo, al suceder una interrupción el microcontrolador pasa automáticamente al modo de ejecución Privileged Handler. 

En cambio, al hacer uso de un RTOS, el modo de operación es el de Unprivileged Thread, en el cual los procesos tienen acceso restringido a recursos del uC, y al ocurrir una interrupción el uC pasa al modo Privileged Thread.  

Un ejemplo de paso del modo privilegiado al no privilegiado y luego de nuevo al privilegiado podría ser el caso en el que un RTOS se encuentra atendiendo una interrupción o excepción, luego una vez finalizada retoma la ejecución no privilegiada, y cuando luego surga una nueva interrupción o excepción pasa nuevamente a modo privilegiado. 

7. Un modelo de registros ortogonal es un modelo de arquitectura de computadoras en el que todas las instrucciones de la máquina pueden acceder a todos los registros disponibles con el mismo derecho. Esto implica que no existen restricciones en cuanto a qué registros pueden ser utilizados por qué instrucciones, o cómo se pueden utilizar.

Un ejemplo de un modelo de registros ortogonal es el modelo de registros de la arquitectura RISC. En este modelo, todas las instrucciones tienen la misma longitud y formato, y cada registro puede ser utilizado por cualquier instrucción.

8. Las instrucciones condicionales IT sirven para representar la famosa estructura if-then. Estas estructuras permiten que se verifique una condición y se ejecute la porción de código correspondiente en lugar de ejecutar bloques de código y saltos que retarden la ejecución del programa.

Ejemplo:

9. Las excepciones de los periféricos propios del core del procesador tendran mayor prioridad frente a posibles interrupciones externas. 

Reset: tiene maxima prioridad. Esta excepción ocurre cuando el sistema se inicia o reinicia. Existe el soft-reset y hard-reset. En el caso del soft-reset unicamente se reinicia el stack pointer, mientras que en el hard-reset se reinicia todo el procesador a nivel alimentación.

NMI: son interrupciones que requieren atención apenas suceden, como por ejemplo fallo en el sistema de clock.

Hard Fault: La excepción Hard fault se produce cuando se produce un error grave en el sistema. Esta excepción puede ser causada por una variedad de factores, como una instrucción incorrecta, una división por cero o un acceso a memoria no válido.

10. La pila sirve para almacenar los registros del procesador al suceder un llamado a una función. Además se utiliza para almacenar los parámetros de las funciones y lo que retornen. 

Al pasar a la ejecución de una función, el procesador almacena los registros en la pila y salta a la dirección en la que se encuentre la función. Luego al retornar de la función almacena su valor de retorno en la pila y repone los registros del procesador para retomar la ejecución principal.

