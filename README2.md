# Tripscore: recomendando rutas en la ciudad de Madrid
Como usuarios del transporte público de una gran ciudad como Madrid estamos acostumbrados a no llegar a tiempo a nuestras citas debido a que el autobús se ha retrasado, hemos perdido el enlace con el metro o porque hemos tenido que hacer 4 transbordos para llegar. Estos son sólo algunos ejemplos de lo que pasa a diario en Madrid en relación al uso del transporte público. ¿Qué pasaría si los usuarios pudiesen obtener recomendaciones en función de sus propias preferencias sobre cuál es la mejor ruta que deben tomar? Eso es exactamente lo que hace Tripscore, en base a la recolección y procesamiento de datos históricos de transporte y su comparación con las preferencias de los usuarios, es capaz de recomendar y puntuar las diferentes opciones existentes para una misma ruta. En este caso particular, a través de los datos abiertos de la Empresa Municipal de Transportes de Madrid, Tripscore es capaz de recomendar rutas de los autobuses de la ciudad a partir de las paradas de salida y llegada del usuario y la fecha del viaje.

## Casos de uso
A lo largo del proyecto hemos identificado 3 casos de uso, 2 relacionados con las necesidades de la ciudadanía en lo que concierne al uso y el servicio del transporte público en Madrid y un tercer caso de uso en relación a buenas prácticas en la publicación de datos del dominio:

1) Adolfo vive en muy cerca del Paseo de la Castellana, a la altura del Estadio Santiago Bernabeu. Todos los días debe desplazarse hasta su lugar de trabajo en Medialab-Prado haciendo uso del transporte público. Consultando [Google Maps](https://www.google.es/maps/dir/Estadio+Santiago+Bernab%C3%A9u,+Av.+de+Concha+Espina,+1,+28036+Madrid/Medialab-Prado,+Calle+de+la+Alameda,+Madrid/@40.4300961,-3.7131846,14z/data=!3m1!4b1!4m14!4m13!1m5!1m1!1s0xd4228e23705d39f:0xa8fff6d26e2b1988!2m2!1d-3.6883445!2d40.4530541!1m5!1m1!1s0xd4226288a4fb7f7:0xd69ac9ed8a94df3d!2m2!1d-3.6937908!2d40.4105268!3e3) este le ofrece hasta 4 formas diferentes de llegar a su trabajo pero, aunque la aplicación le ofrece una estipulación del tiempo que tardará en viajar, no sabe muy bien cuál será la ruta que se le adapte mejor a sus necesidades ya que sabe que no tiene en cuenta variables como el tráfico o los habituales parones en el metro. Como ha recibido la noticia de que está semana habrá restricciones de tráfico en Madrid debido a la contaminación ha descartado las opciones del bus y ha escogido la opción del metro. Al utilizar esa opción ha tenido que hacer un transbordo en la estación de Tribunal y, además de tener que subir un montón de escaleras rodeado de mucha gente, ha llegado tarde al trabajo debido a que se ha encontrado la línea que le llevaba al trabajo cerrada y no le ha quedado más remedio que subirse a un taxi. Al día siguiente, y aun sabiendo que habrá tráfico, escoge la opción del autobús ya que no tiene que hacer ningún intercambio entre líneas y le deja muy cerca de Medialab-Prado. Aunque se retrasó 10 min en comparación con el tiempo que le había proporcionado Google Maps, tiene claro que es mejor que tener que coger un taxi. Adolfo ha buscado en la tienda de aplicaciones de su smartphone otras aplicaciones de transporte para Madrid, pero todas se parecen mucho a Google Maps y no le cubren las necesidades que él tiene, ni tienen en cuenta las preferencias que, como usuario, demanda del servicio.

2) Ana se acaba de mudar a Madrid para hacer un máster en la Escuela de Ingenieros Informáticos de la Universidad Politécnica de Madrid. Ha encontrado un piso dónde vivir entre las estaciones de Metro de Alonso Cano y Ríos Rosas. Nada más llegar a la ciudad, Ana se ha hecho con un abono de transporte público ya que todos los días tendrá que desplazarse desde el centro de la ciudad hasta cerca de Boadilla del Monte para ir a clase. Ana quiere saber cuál es la forma más rápida de llegar desde su casa a la facultad ya que tiene, en función de la información facilitada por la escuela, hasta 9 formas diferentes de llegar. Al consultar con Google Maps, se da cuenta que no le da la opción de coger buses interurbanos para llegar la Universidad, es por ello que el primer día decide coger el metro hasta Colonia Jardín y a continuación el Metro Ligero. La duración del viaje ha sido de 1 hora y 10 minutos, por lo que piensa que debe haber alguna opción mejor y se descarga en su smartphone una aplicación de autobuses interurbanos de la ciudad. Al día siguiente la duración de su viaje es de 50 minutos, por lo que está bastante satisfecho y decide tomar esa ruta siempre. Lo que Ana no sabe, es que no está cogiendo la ruta más rápida para llegar a la facultad. Si pudiese obtener esa información de alguna manera, se ahorraría todos los días 10 minutos en cada viaje.

3) Datasetito es un conjunto de datos abiertos en [GTFS](https://developers.google.com/transit/gtfs/?hl=es-419) que representa los datos de transporte de la Empresa Municipal de Transportes de Madrid (EMT). Datasetito está muy triste porque, aunque es un conjunto de datos que puede ser consultado por cualquiera al ser abierto, salvo Google Maps, que ha sido implementado para trabajar con este formato, ningún desarrollador lo tiene en cuenta al implementar sus aplicaciones debido a su complejidad y dificultad en su procesamiento. Datasetito se ha puesto a buscar soluciones en la web que le permitan mejorar su formato ya que la información que ofrece es muy interesante para los ciudadanos y cree que los desarrolladores deberían tenerlo en cuenta en sus aplicaciones. Buscando y buscando se ha topado con el paradigma de los [Datos Enlazados o Linked Data](https://es.wikipedia.org/wiki/Datos_enlazados) y se ha dado cuenta de que sería la mejor forma de publicar sus datos, siguiendo una representación de los datos consensuada entre expertos y dotando a todos sus recursos de identificadores únicos en la web o [URIs](https://es.wikipedia.org/wiki/Identificador_de_recursos_uniforme). Así, Datasetito, se ha puesto a buscar representaciones de datos enlazados en el dominio del transporte y ha encontrado unos chicos muy majos que llevan trabajando en algo llamado [Linked Connections](http://linkedconnections.org/) desde hace unos años y están pidiendo conjuntos de datos para realizar pruebas. Además, Datasetito no está preocupado por su actualización semanal, ya que los chicos de Linked Connections le han demostrado que puede seguir publicándose en la página web de la EMT ya que directamente lo procesan a partir de esa dirección. Finalmente, Datasetito ha contactado con el grupo de Ingeniería Ontológica de la Universidad Politécnica de Madrid (co-creadores de Linked Connections) para realizar la transformación y publicación de sus datos.


## La solución: Tripscore
Tripscore es una aplicación web que se puede ejecutar tanto en un navegador web como a través de cualquier smartphone que tenga acceso a internet. A través de ella se puede consultar múltiples datos sobre las diferentes rutas de los autobuses de la EMT como por ejemplo el tiempo medio del viaje, el número de transbordos necesarios para llegar al destino o la media del tiempo que la ruta se suele retrasar. Además, cada usuario puede configurar sus propias preferencias como el tiempo aceptable de retraso en una ruta o el tiempo necesario para realizar intercambios entre rutas. Estas preferencias influirán en la puntuación de cada una las rutas con un sistema de estrellas con la idea de ofrecer al usuario la ruta que más se acomode a sus prioridades. Para llevar a cabo esta idea se han implementado tres partes diferenciadas: el cliente o aplicación web que consume datos enlazados de transporte, el servidor que proporciona dichos datos enlazados siguiendo el vocabulario de Linked Connections y, por último, una API que contiene información sobre las paradas o estaciones de cada una de las empresas que se pueden consultar a través del cliente. A continuación detallamos cada una de esas partes:


### El desarrollo

#### El cliente de datos enlazados Tripscore
El cliente Tripscore es una aplicación web, accesible en [http://tripscore.lab.oeg-upm.net/](http://tripscore.lab.oeg-upm.net/), que se conforma de tres páginas diferentes:
1) La página inicial, en dónde el usuario puede escoger el país, la ciudad o el conjunto de datos que quiere consultar las estaciones de salida y llegada y la fecha del viaje. Además, en la parte izquierda de la pantalla se mostrarán los viajes más consultados por el usuario. En la imagen se muestra un ejemplo:

![La imagen no ha cargado](https://github.com/medialab-prado/tripscore/blob/master/imagenes/tripscore.png)

2) La página de preferencias del usuario, dónde, a través de un cuestionario cubierto por más de 50 usuarios se han recolectado las preferencias más relevantes que se debían tener en cuenta a la hora de puntuar las rutas de transporte. Cada una de las preferencias se acompaña con una explicación de la misma.

![La imagen no ha cargado](https://github.com/medialab-prado/tripscore/blob/master/imagenes/preferencias.png)

3) La página que muestra las diferentes rutas en función de la fecha y las estaciones de salida y llegada que el usuario ha introducido en la página inicial. Cada ruta encontrada se puntúa en función de las preferencias que el usuario haya establecido. Por ejemplo, si el usuario ha establecido que acepta que la ruta se suela retrasar una media de 5 minutos pero no acepta que haya que realizar ningún transbordo para llegar a su destino, las rutas con transbordo y que se retrasen una media de más de 5 minutos tendrán una puntuación más baja que las demás. Se puede ver un ejemplo en la siguiente imágenes:

![La imagen no ha cargado](https://github.com/medialab-prado/tripscore/blob/master/imagenes/rutas2.png)

![La imagen no ha cargado](https://github.com/medialab-prado/tripscore/blob/master/imagenes/rutas1.png)


#### El servidor de Linked Connections
Este servidor es el encargado de transformar y proveer de un valor añadido a los datos proporcionados por la EMT en GTFS. Obteniendo los datos directamente desde la [fuente](http://opendata.emtmadrid.es/Datos-estaticos/Datos-generales#GoogleTransit) los transforma y publica siguiendo el vocabulario propuesto por Linked Connections, que se centra en modelar una conexión entre dos puntos. Al publicar los datos de esta manera, se consigue que cualquier aplicación, cliente o software pueda acceder a los mismos de una manera rápida y sencilla comprendiendo perfectamente la semántica de la información que se proporciona. Así, se mejora la interoperabilidad entre diferentes fuentes de datos y se ofrece la posibilidad de consultar datos abiertos enlazados de muchas compañías de transporte sin la necesidad de que ninguna compañía o institución tenga que modificar sus datos o cambiar el formato de los mismo ya que actualmente GTFS es un estándar de facto y la mayoría de datos de transporte se exponen siguiendo este formato. Para acceder a estos datos se puede utilizar el siguiente ejemplo:

```http
http://tripscore.lab.oeg-upm.net/server/emt/connections?departureTime=YYYY-MM-DDThh:mm:ss.000Z
```

En dónde el parámetro "departureTime" establece la fecha y hora de los datos que se quieren mostrar. Cada consulta mostrará 10 minutos de conexiones en formato JSON-LD. En la siguiente imagen se puede ver un ejemplo de los [datos obtenidos para el día 27 de Noviembre de 2017 a las 16:30 de la tarde](http://tripscore.lab.oeg-upm.net/server/emt/connections?departureTime=2017-11-27T16:30:00.000Z). Sobre el funcionamiento del servidor e información de sus características más detalladas se pueden obtener accediendo al [siguiente enlace](https://github.com/dachafra/my-linked-connections-server) (en inglés).

![La imagen no ha cargado](https://github.com/medialab-prado/tripscore/blob/master/imagenes/linkedconnections.png)


#### API con información de las paradas

## Trabajo futuro
El desarrollo de la aplicación no terminará con la finalización del DataMad. 


## Colaboradores
David Chaves - [@dchavesf](https://twitter.com/dchavesf)  
Oscar Orlando - [@oscarceballos](https://github.com/oscarceballos)   
Victor Fernández - [@vfrico](https://github.com/vfrico) 


## Agradecimientos
Queremos agradecer a [Carlos Badenes](https://github.com/cbadenes) y Raúl Alcazar, miembros del OEG, por su ayuda para crear todo el ecosistema desarrollado con Docker y Rancher.




