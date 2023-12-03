---
layout: home
title: Pick to Pharmacy
---

## Introducción
---
En el presente proyecto se propone desarrollar y construir un sistema semejante al “Pick to Light” ya existente, añadiendo IoT (Internet of things) implementando sensores y actuadores, con el fin de proporcionar una mayor eficiencia y un mejor control al trabajo de los empleados farmacéuticos.

---
## Objetivos
---
### Los objetivos del trabajo son:

>- Construir un prototipo a escala que represente el “Pick to Pharmacy”.
>- Implementar una conexión satisfactoria con la nube a utilizar (Thingsboard), realizando acciones a través de esta y recibiendo respuestas del sistema.
>- Integrar sensores y actuadores para monitorear y controlar el inventario de medicamentos en tiempo real.
>- Optimizar los procesos de recolección de medicamentos al guiar al personal hacia los productos correctos mediante luces indicadoras.
>- Implementar un panel para pedido de compra de los productos.
 
---
## Descripción 
---
### *Problema:* 
En el sector farmacéutico, la gestión de stock y la seguridad de los medicamentos son cuestiones de suma importancia. En particular, la de aquellos medicamentos de receta verde, los cuales requieren una prescripción de un profesional de la salud autorizado previa a su compra, dado a sus efectos secundarios y riesgos para la salud.
Por lo tanto mantener un buen manejo del inventario, implica que los fármacos se encuentren en buen estado, disponibles y seguros. Evitando así el riesgo de que se encuentren en malas condiciones, pérdida, hurto o mal uso.

### *Solución:*
Para estos problemas se diseñó una solución eficaz y práctica. La cual consiste en un sistema de recolección bajo control profesional de pedidos de medicamentos. Permitiendo guiar con una led, al trabajador hacia sector de la estantería donde se encuentra el producto solicitado por el cliente, indicando en una pantalla LCD el nombre del medicamento y la cantidad específica de medicamentos a llevar de ese tipo. Asimismo, para que sea seguro saber quién extrae el medicamento y si está autorizado, cada sección de la estantería consta con una lámina transparente que cubre los fármacos, que solamente se podrá acceder a ellos con una tarjeta de RFID, validando así su extracción. Al pasar la tarjeta, se accionaran los motores que abrirán las compuertas para poder retirar los medicamentos. Al terminar, el trabajador tendrá que presionar un botón para que se verifique si la acción realizada fue correcta, en caso de éxito se cerrarán las compuertas y en caso contrario en el mismo display se mostrará un aviso de error, con el fin de alertar al empleado que no concluyó su trabajo exitosamente.


![](assets/manualdeusuario.png)


### *Implementación:*

El desarrollo de este proyecto se dividirá en dos grandes partes, software y hardware. 
La primera respectivamente consiste en implementar una conexión a “ThingsBoard”, para la gestión y visualización de datos extraídos de las estanterías, proporcionando de forma rápida y sencilla información acerca de quiénes fueron aquellos empleados que interactuaron con determinados medicamentos. Se pretende que “ThingsBoard” realice las intervenciones correspondientes sobre el prototipo, ya sea prendiendo los LEDs, indicando las cantidades y posteriormente moviendo los actuadores.
Con el propósito de que el usuario se comunique con la empresa para realizar su pedido de compra, se creará un panel interactivo para que éste ingrese la cantidad de medicamentos que desea encargar.

La segunda parte estará compuesta de un sistema de estanterías a escala con sus respectivos actuadores y sensores.
Para poder acceder a un medicamento, el empleado tendrá que leer su tarjeta de identificación mediante RFID (Radio Frequency Identification), la cual permitirá que actúe un motor que hará que se abra una compuerta, para así acceder a ellos.
Respecto al modelado de las estanterías y sus compartimientos, van estar dispuestos de forma inclinada. De esta manera la gravedad actuará sobre los medicamentos y estos podrán bajar sin la necesidad de que alguna fuerza externa interactúe. Dentro de este se encontrará un sensor de ultrasonido, para medir la distancia que hay entre la pared y el último medicamento, con el fin de lograr un control de stock y conseguir una exitosa verificación para cuando se retiren los medicamentos.
De la cara exterior al compartimiento, se va disponer de una pantalla LCD que le indicará al empleado cuántos medicamentos se requieren para el pedido que se solicita. A su vez acompañado de una LED que tiene como función indicar en qué zona de la estantería se está requiriendo el medicamento del pedido, esto hace alusión al “Pick to Light”.
Por último, se coloca al final de la estantería un botón que tiene como función apagar estos y activar el actuador para cerrar las compuertas de los medicamentos, verificando que efectivamente estos hayan sido retirados satisfactoriamente.
Las dimensiones de la estantería y sus compartimientos serán vistos más adelante, ya que dependen de los materiales a utilizar.

---
## Prototipo
----

![](assets/prototipo1.png)


![](assets/prototipo2.png)


![](assets/prototipo3.png)

---
## Planificado
---
#### Pruebas de Concepto:

- Investigación ThingsBoard: 
    - Adquirir un conocimiento profundo del funcionamiento de la plataforma.

- Desarrollo de Software:
    - Sensores: 
        - Buscamos un código en internet para ver su funcionamiento como tal.
        - Adaptamos el código encontrado, con el fin de que se comunicará con ThingsBoard para si realizar una transmición de datos.
        - Calibrar la cantidad de medicamentos mediante cálculos y utilizarla como atributo modificable según el tipo de medicamento.
    - RFID:
        - Buscamos un código en internet para ver su funcionamiento como tal.
        - Adaptamos el código encontrado, con el fin de que se comunicará con ThingsBoard, para si realizar una transmición del número Hexadecimal de la tarjeta. Para que luego ese digito fuera agregadado y identificado como una tarjeta habilitada a retirar fármacos.
        - Lograr la identificación de frecuencias para habilitar adecuadamente a los empleados.
    - Pantallas LCD: 
        - Buscamos un código en internet para ver su funcionamiento como tal.
        - Desarrollar el código encontrado, con el objetivo de colocar los nombres de los medicamentos y sus respectivas cantidades, las cuales se actualizan en cada pedido. 
    - Motores :
        - Buscamos un código en internet para ver su funcionamiento como tal.
    - Arduino Mega:
        - Implementamos una comunicación serial entre el Arduino Mega y la esp8266, con la intención de que la esp8266 transmita las ordenes a la placa de Arduino Mega. Esto fue necesario ya que la esp8266 no nos podía sutir con la cantidad de pines necesarios.
    - Leds:
        - Buscamos un código en internet para ver su funcionamiento como tal.
        - Realizamos respectivas funciones de apagado y prendido en el código. Se prenderán indicando que zona de la estantería se requiere extraer medicamentos y luego se apagarán después de cerrarse las compuertas.
    - Botones:
        - Buscamos un código en internet para realizar el Debounce.
        - Envía las cantidadeds actulizadas de los medicamentos retirados, con el objetivo de confirmar su exitosa extración. 
    - Conexión con ThingsBoard:
        - Utilizamos un código brindado por los docentes, apartir de este implementamos la comunicación entre los componentes.
    - Creación de un Panel: 
        - Desarrollar un panel público dentro de ThingsBoard para que los clientes realicen pedidos y apartir de esto comunicar las instrucciones a los empleados.


#### Prototipo 1:
- Una estantería inteligente, que prenda Leds en la zonas que se requiere retirar medicamentos. Va a poseer un RFID capaz de leer una tarjeta, la cual si esta ingresada como habilitada accione los motores para que abran las compuertas así se logrando retirar los medicamentos. También que integre una Pantalla Lcd que muestre los nombres y cantidades de medicamentos a extraer. 
Luego de realizar estas acciones, se presione un botón que envíe los datos actulizados, obtenidos de los sensores de distancia. Con el fin de confirmar que ya se retiraron adecuadamente lo solicitado en el pedido. Si fue exitoso que se reseten las cantidades y en caso contrario que muestre error en las pantallas Lcd.
A su vez posee una estructura adecuada para integrar estos componentes.

#### Prototipo 2:
- Es lo mismo que el prototipo 1, pero incluye implentación de APIs. El cual no realizamos.

#### Problemas y riesgos:
- No alcanzaron los pines en la esp8266, por lo tanto tuvimos que utilizar la Arduino Mega para poder conectar todos los elementos.
- Algunas veces al tener tantos componentes conectados a la vez, no sabíamos de donde origanaba el problema. 
- En ocaciones se genero un loop en la cadena de reglas dentro de ThingsBoard. Esto provocaba que pasaramos el limite de operaciones en la demo, por consecuencia ya no nos podíamos conectar por una cantidade de tiempo determinado.


---
## Los Experimentos
---
### Materiales empleados: 
- Placa esp8266
- Placa Arduino Mega
- 4 Leds
- 4 Pantalla LCD
- 1 Botón
- 4 Sensores de distancia
- Cables
- 4 Motores
- Fuente
- Resistencias 1kohm y 100 omhs
- RFID
- Materiales de estructura
- ThingsBoard

### Material consultado:

- [Placa esp8266 pinOut](https://randomnerdtutorials.com/esp8266-pinout-reference-gpios/)
- [datasheet esp8266](https://www.espressif.com/sites/default/files/documentation/0a-esp8266ex_datasheet_en.pdf)
- [Placa Arduino Mega](https://docs.arduino.cc/resources/datasheets/A000067-datasheet.pdf)
- [Direcciónes I2C para las pantallas LCD](https://lastminuteengineers.com/i2c-lcd-arduino-tutorial/#google_vignette)
- [Motores datasheet](https://datasheetspdf.com/pdf-file/1106582/ETC/MG90S/1)
- [Sensores datasheet](https://datasheetspdf.com/pdf-file/1380136/ETC/HC-SR04/1)
- [Pantalla LCD](https://lastminuteengineers.com/i2c-lcd-arduino-tutorial/#google_vignette)
- [RFID datasheet](https://pdf1.alldatasheet.com/datasheet-pdf/download/346106/NXP/MFRC522.html)
- [ThinsBoard documentación](https://thingsboard.io/docs/)

### Enlaces a los códigos del prototipo: 
- [Código Arduino de esp2866](https://github.com/SisCom-PI2-2023-2/proyecto-pick-to-pharmacy/blob/main/Probando%20nueva%20cadena%20de%20reglas)
- [Código Arduino Mega](https://github.com/SisCom-PI2-2023-2/proyecto-pick-to-pharmacy/blob/main/Arduino%20codigo)


### Después se incluira fotos del resultado final

### Conocimientos adquiridos:

Hemos adquirido diversas habilidades a lo largo del proyecto, entre las cuales se incluyen:

- La aplicación efectiva de conexiones MQTT para facilitar la comunicación entre dispositivos.

- La manipulación experta de variables en formato JSON, permitiéndonos una gestión eficiente de datos.

- La adopción del método de trabajo Scrum, que ha mejorado significativamente la organización y eficiencia en el desarrollo del proyecto.

- La utilización hábil de servicios en la nube y GitHub, brindándonos herramientas para el almacenamiento y colaboración en línea.

- La implementación exitosa de una conexión serial entre dos placas diferentes, demostrando nuestra capacidad para integrar y comunicar dispositivos de manera efectiva.

- La colaboración y coordinación efectiva en equipo, destacando la importancia del trabajo conjunto para lograr nuestros objetivos de manera eficiente y satisfactoria.

---
## Bitácora 
---
