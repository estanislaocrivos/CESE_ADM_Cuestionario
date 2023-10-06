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

9. Las excepciones de los periféricos propios del core del procesador tendran mayor prioridad frente a posibles interrupciones externas. 

Reset: tiene maxima prioridad. Esta excepción ocurre cuando el sistema se inicia o reinicia. Existe el soft-reset y hard-reset. En el caso del soft-reset unicamente se reinicia el stack pointer, mientras que en el hard-reset se reinicia todo el procesador a nivel alimentación.

NMI: son interrupciones que requieren atención apenas suceden, como por ejemplo fallo en el sistema de clock.

Hard Fault: La excepción Hard fault se produce cuando se produce un error grave en el sistema. Esta excepción puede ser causada por una variedad de factores, como una instrucción incorrecta, una división por cero o un acceso a memoria no válido.

10. La pila sirve para almacenar los registros del procesador al suceder un llamado a una función. Además se utiliza para almacenar los parámetros de las funciones y lo que retornen. 

Al pasar a la ejecución de una función, el procesador almacena los registros en la pila y salta a la dirección en la que se encuentre la función. Luego al retornar de la función almacena su valor de retorno en la pila y repone los registros del procesador para retomar la ejecución principal.

11. El primer paso es la inicialización del Stack Pointer (SP) que apunta a la dirección de inicio de la pila. Luego, el Program Counter (PC) se configura para apuntar al vector de reset. El vector de reset es una dirección de memoria fija que contiene la dirección de inicio del programa principal después del reset. Una vez que el PC apunta al vector de reset, se inicia la ejecución del programa principal desde la dirección de memoria especificada en ese vector.

12. Los Core Peripherals son los periféricos internos al núcleo del microprocesador y son escenciales para llevar a cabo las principales funciones del microprocesador. Une ejemplo de este tipo de periféricos es el NVIC (Nested Vector Interrupt Controller). Este es un controlador de interrupciones que gestiona las interrupciones del sistema y permite priorizar y controlar cómo se manejan las interrupciones en el microcontrolador. La diferencia de estos periféricos con los periféricos convencionales del uC es que estos últimos vienen a proveer funciones adicionales al uC pero que no son esenciales para su funcionamiento básico. Un periférico de este tipo puede considerarse la unidad de punto flotante por HW que integran los Cortex M4. 

13. Las excepciones de los Core Peripherals siempre tendrán mayor prioridad que las interrupciones externas. Por ejemplo una excepción por Reset va a tener mucha mayor prioridad que una interrupción por un ADC del uC. 

14. El CMSIS es una capa de abstracción de HW que corre en los Cortex M, con el objetivo de darle portabilidad al código entre distintos procesadores ARM Cortex. Brinda herramientas para que el core interactúe con los Core Peripherals y un RTOS.

15. Al ocurrir una interrupción mientras el uC se encuentra en el modo de ejecución no privilegiado primero debe hacer un Stacking del estado del procesador en el momento en que ocurre la interrupción. Esto implica guardar el contenido de los registros y el contador de programa (PC) actual en una pila o en registros específicos de almacenamiento temporal. Luego, el microprocesador utiliza una tabla de vectores de interrupción o una dirección específica de memoria para determinar la dirección de inicio de la subrutina de interrupción correspondiente. Esta dirección se carga en el contador de programa (PC) del microprocesador. Después de que la subrutina de interrupción ha completado su trabajo, se restaura el estado del procesador al punto en el que se encontraba antes de la interrupción. Esto implica recuperar los registros y el PC del estado guardado previamente.

16. La FPU generalmente tiene un registro de estado que controla y registra el estado actual de las operaciones de punto flotante, incluidas las banderas de estado (por ejemplo, bandera de cero, bandera de sobreflujo, etc.). Este registro de estado también se considera en la operación de stacking. Es decir, en este caso el stacking involucra más registros.

17. El Tale Chaining es un proceso que se ejecuta cuando llega una interrupción en el momento en el que se esta ejecutando otra ISR. En este caso no se hace Context Switching. El Late Arrival se da cuando se esta ejecutando una ISR y surge una interrupción de mayor prioridad. 

18. El SysTick es un temporizador de sistema (System Tick Timer) que se encuentra en muchos microcontroladores basados en la arquitectura ARM Cortex-M. Su implementación favorece la portabilidad de los sistemas operativos embebidos porque proporciona una fuente de temporización precisa y regular que se puede utilizar para generar interrupciones periódicas a intervalos regulares de tiempo. Esto es esencial para tareas como el control de tiempo en sistemas embebidos, programación de tareas periódicas y medición de intervalos de tiempo. Además este temporizador se encuentra en gran parte de los procesadores de la familia Cortex M lo cual facilita la portabilidad.

19. La función principal de este módulo es proteger el acceso a memoria. Además, previene que las aplicaciones (tareas) accedan a zonas de memoria de otras aplicaciones o del kernel de un SO, que las aplicaciones accedan a periféricos sin los permisos adecuados o que se ejecute código desde zonas no permitidas (ejemplo desde la RAM).

20. Se pueden proteger hasta 8 regiones. En la mayoría de los casos, si se configuran regiones que se solapan, se aplicarán los permisos de acceso más restrictivos. Es decir, si una dirección de memoria está cubierta por varias regiones, se aplicarán las restricciones más estrictas de entre esas regiones. Las zonas de memoria que no están cubiertas por ninguna región definida generalmente estarán sujetas a los permisos predeterminados o valores de acceso que establezca el hardware o el sistema operativo. 

21. La excepción PendSV (Pendable Supervisor Call) se utiliza comúnmente en microprocesadores ARM Cortex-M. Su principal propósito es permitir la planificación de tareas en sistemas multitarea en tiempo real. Se relaciona con otras excepciones, como SysTick y las interrupciones de hardware, para proporcionar una gestión eficiente de tareas en sistemas embebidos.

Supongamos un sistema embebido con un sistema operativo en tiempo real (RTOS) que administra múltiples tareas. El planificador de tareas decide que es el momento de cambiar de una tarea a otra para dar tiempo de ejecución a diferentes procesos. Se activa PendSV para realizar este cambio de contexto. Ejemplo:

La tarea actual ha estado ejecutando durante un tiempo y el planificador de tareas decide que otra tarea debe ejecutarse a continuación.
El planificador de tareas activa la excepción PendSV por software.
PendSV se ejecuta en la prioridad más baja, y su código se encarga de guardar el contexto de la tarea actual en la pila de esa tarea.
Luego, PendSV carga el contexto de la siguiente tarea que debe ejecutarse desde su pila.
El sistema cambia de contexto y comienza a ejecutar la nueva tarea, que continúa su ejecución desde donde se detuvo la última vez.

22. La excepción SVC (Supervisor Call) se utiliza en sistemas embebidos, especialmente en sistemas operativos en tiempo real (RTOS), para proporcionar una interfaz entre el código de la aplicación y el núcleo del sistema operativo. También se conoce como "syscall" o "trap" en otros contextos.