---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
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
Para estos problemas se diseñó una solución eficaz y práctica. La cual consiste en un sistema de recolección bajo control profesional de pedidos de medicamentos. Permitiendo guiar con una led, al trabajador hacia sector de la estantería donde se encuentra el producto solicitado por el cliente, indicando en una pantalla Led el nombre del medicamento y la cantidad específica de medicamentos a llevar de ese tipo. Asimismo, para que sea seguro saber quién extrae el medicamento y si está autorizado, cada sección de la estantería consta con una lámina transparente que cubre los fármacos, que solamente se podrá acceder a ellos con una tarjeta de RFID, validando así su extracción. Al pasar la tarjeta, se accionaran los motores que abrirán las compuertas para poder retirar los medicamentos. Al terminar, el trabajador tendrá que presionar un botón para que se verifique si la acción realizada fue correcta, en caso de éxito se cerrarán las compuertas y en caso contrario en el mismo display se mostrará un aviso de error, con el fin de alertar al empleado que no concluyó su trabajo exitosamente.

### *Implementación:*

El desarrollo de este proyecto se dividirá en dos grandes partes, software y hardware. 
La primera respectivamente consiste en implementar una conexión a “ThingsBoard”, para la gestión y visualización de datos extraídos de las estanterías, proporcionando de forma rápida y sencilla información acerca de quiénes fueron aquellos empleados que interactuaron con determinados medicamentos. Se pretende que “ThingsBoard” realice las intervenciones correspondientes sobre el prototipo, ya sea prendiendo los LEDs, indicando las cantidades y posteriormente moviendo los actuadores.
Con el propósito de que el usuario se comunique con la empresa para realizar su pedido de compra, se creará un panel interactivo para que éste ingrese la cantidad de medicamentos que desea encargar.

La segunda parte estará compuesta de un sistema de estanterías a escala con sus respectivos actuadores y sensores.
Para poder acceder a un medicamento, el empleado tendrá que leer su tarjeta de identificación mediante RFID (Radio Frequency Identification), la cual permitirá que actúe un motor que hará que se abra una compuerta, para así acceder a ellos.
Respecto al modelado de las estanterías y sus compartimientos, van estar dispuestos de forma inclinada. De esta manera la gravedad actuará sobre los medicamentos y estos podrán bajar sin la necesidad de que alguna fuerza externa interactúe. Dentro de este se encontrará un sensor de ultrasonido, para medir la distancia que hay entre la pared y el último medicamento, con el fin de lograr un control de stock y conseguir una exitosa verificación para cuando se retiren los medicamentos.
De la cara exterior al compartimiento, se va disponer de una pantalla Led que le indicará al empleado cuántos medicamentos se requieren para el pedido que se solicita. A su vez acompañado de una LED que tiene como función indicar en qué zona de la estantería se está requiriendo el medicamento del pedido, esto hace alusión al “Pick to Light”.
Por último, se coloca al final de la estantería un botón que tiene como función apagar estos y activar el actuador para cerrar las compuertas de los medicamentos, verificando que efectivamente estos hayan sido retirados satisfactoriamente.
Las dimensiones de la estantería y sus compartimientos serán vistos más adelante, ya que dependen de los materiales a utilizar.

---
## Prototipo
----

![](assets/prototipo1.png)


![](assets/prototipo2.png)


![](assets/prototipo3.png)
