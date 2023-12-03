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

Otra de las ideas originales del proyecto que no llegaron a ser implementadas fue la del control de fechas de vencimiento. En un principio, se pretendía que el sistema conozca las fechas de vencimiento de todos los medicamentos en las estanterías y que notifique al personal (mediante las leds o una api) cuando se hubieran vencido los productos. Luego de familiarizarnos un poco más con thingsboard encontramos que el límitado manejo de bases de datos de la herramienta hacia del control del stock tan detallado como pretendíamos sería muy complicado y tomaría muchisimo tiempo, por ésto decidimos no llegamos a implementa el manejo de fechas de vencimiento, optando únicamente por controlar la cantidad de medicamentos de cada tipo que tiene la góndola.

### Distinción de empleados

La distinción entre los distintos empleados del sistema es una función del sistema que perdió un poco de utilidad al hacer un único módulo cómo prototipo. En un principio los empleados estarían no solo asociados a l número de su tarjeta RFID sino a un color de led que indicaría quien debe tomar el pedido. La distinción entre empleados se puede también aplicar de manera que determinados empleados tengan acceso a determinados estantes. Y en caso de tener varías estanterías, se podrían hacer grupos de estanterías (utilizando activos) a las cuales determinados empleados pueden acceder. Éste tipo de mejoras, de manera similar a lo hablado en la parte de modularización, no suponen un cambio muy drástico del funcionamiento del sistema en thingsboard ya que actualmente ya funciona de manera muy similar.

### Envío de pedidos, página/app

Para recibir pedidos se pretendía usar una página web o mas probablemente una aplicación de celular con la cual un cliente pudiera seleccionar las cantidades de los productos que desea comprar y que éstas se envíen a thingsboard. Para simplificar la comunicación del pedido con thingsboard se terminó optando por utilizar un dashboard público en el cual se seleccionan las cantidades del pedido, éste automaticamente las guarda en thingsboard iniciando el proceso de recepción de pedido.

### APIs

Se pretendía en un principio utilizar APIs de calendario y mensajería (mail o sms) para notificar de determinadas cosas. Ésto iba de la mano de la implementación del control de fechas de vencimiento por ejemplo que al final no se implementó, o también para notificar sobre cosas cómo la falta de stock de algún producto determinado o para recibir los pedidos desde una aplicación. Al final, en parte debido a que no se implementó el control de fechas de vencimiento ni la aplicación para envíar pedidos, lo que disminuyó su utilidad, y por falta de tiempo, no llegamos a investigar sobre el funcionamiento de éstas APIs en thingsboard.

### Calibración de sensores

A la hora de calibrar los sensores de distancia se fijan dos constantes que despenden del tamaño de las cajas y del stock máximo de cada medicamento. Estos valores nos permiten, utilizando la medida en centímetros del sensor, obtener la cantidad de medicamentos que hay en el estante. Éstos valores de calibración actualmente están escritos en la placa y no se pueden cambiar sin acceder a ella y cambiar el código. Entendemos que lo mejor, y una posible mejora, es que estos valores se guarden en la nube.

Si las constantes de calibración estuvieran en la nube, permitiría cambiar los productos que se venden en una estantería sin tener que acceder a la placa y cambiar las constantes en el código. Sin embargo, sería necesario que la placa pida estas constantes a thingsboard cada vez que se resetea, ésto es algo que simplemente no tuvimos tiempo de implementar sobre el final del proyecto con lo que las constantes quedarán fijas en la placa.
