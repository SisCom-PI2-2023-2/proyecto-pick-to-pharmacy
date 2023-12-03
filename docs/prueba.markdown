---
layout: page
title: Oportunidades de mejora
permalink: /aprendizaje/
---

## Oportunidades de mejora

Durante el transcurso del semestre, hubieron varios cambios al diseño original del proyecto asi cómo funcionalidades que no llegaron a ser implementadas. A continuación describiremos los más importantes, explicando las causas yu las posibles mejoras que se podrían hacer a futuro.

### Modularización

Uno de los principales cambios al diseño del prototipo fue la no implementación de un ejemplo de modularización. Originalmente el protopipo consistía de dos estanterías iguales con dos medicamentos distintos, ambas conectadas al sistema de thingsboard. De ésta forma se mostraba la posibilidad de escalado del proyecto, pudiendo llegar a tener en teória cualquier cantidad de módulos de estanterías. 

Finalmente, debido a disponibilidad de materiales y los límites de tiempo se decidió hacer un sólo módulo con cuatro medicamentos distintos. De esta manera se simplificaron varias cosas. El módulo entero usa un sólo RFID, mientras que los dos mosulos habrían necesitado uno cada uno, tan solo ésto ocupaba tanto lugar en la placa que hubieran sido necesarias dos placas por cada módulo para hacerlo posible.

Si bien la complejidad de construcción del prototipo es bastante mayo al hacer varios módulos, desde el lado del servidor el funcionamiento es practicamente igual. Con mínimas modificaciones, y agregando más dispositivos a thingsboard se pueden agregar módulos manteniendo la cadena de reglas prácticamente igual. De ésta forma podríamos también agregar módulos cómo el que finalmente hicimos y, con cambios mínimos o practicamente nulos al funcionamiento de thingsboard, lograr la isma idea de modularización que se había propuesto originalmente.

### Fechas de vencimiento

Otra de las ideas originales del proyecto que no llegaron a ser implementadas fue la del control de fechas de vencimiento. En un principio, se pretendía que el sistema conozca las fechas de vencimiento de todos los medicamentos en las estanterías y que notifique al personal (mediante las leds o una api) cuando se hubieran vencido los productos. Luego de familiarizarnos un poco más con thingsboard encontramos que el límitado manejo de bases de datos de la herramienta hacia del control del stock tan detallado como pretendíamos sería muy complicado.

---

Encabezados

# Encabezado

## Encabezado

### Encabezado

#### Encabezado

##### Encabezado

---

Imagen:

![mtstmichel](/assets/mtstmichel.jpg)

---

Listas

   1. Primer punto
   2. Segundo punto
   3. ...


   * Lista no ordenada
   * con muchos puntos
   * ...

---

Quotes

   > Cita o recuadro


