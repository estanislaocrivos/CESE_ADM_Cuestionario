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