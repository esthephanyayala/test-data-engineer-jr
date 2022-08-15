# Ejercicio práctico para Data Engineer Jr en Deacero. - Respuestas



##### 1. Se tiene un requerimiento de análisis de las fuentes de datos de pasajeros y viajes. Como podrás observar, las listas se han estado llevando por año. En esta primera parte del reto se te pide:

- Unir cada conjunto de datos en una sola lista.
- Explicar el proceso realizado.
- En caso de detectar anomalías generadas por esta unión, deberás indicar el tipo de anomalía que se presenta, como se puede resolver y resolverlo de ser posible.

> Para la unión de Pasajeros 2016 X Pasajeros 2017 y Vuelos 2016 X Vuelos 2017  se realizó una concatenación simple. Se decidió hacerlo de esta manera ya que la informacion de Pasajeros y Vuelos de cada año cuentan con las mismas cantidad de columnas y mismo tipos de datos. 

> En el caso de Pasajeros, las anomalias que se detectaron fueron pasajeros con ID duplicados y pasajeros que compartian el mismo ID, para resolverlo se eliminaron los ID duplicados ( exportaron a csv para análisis manual)
Con el DataFrame Vuelos, se detectó una anomalia de un cliente que realizó dos viajes el mismo dia, misma aerolínea y misma ruta pero con clase diferente. En este caso no se realizó ningún cambio ya que se desconoce si en realidad es un error de captura o es información correcta. 

##### 2. De lo obtenido anteriormente se requiere relacionar las listas de vuelos y pasajeros, que permitan analizar el perfil del pasajero por cada vuelo efectuado. De tal forma que se puedan obtener datos consolidados. En esta parte deberás:

- Explicar el proceso que utilizado para unir los pasajeros y los vuelos.
- Qué tipo de relación y por qué.

> Para poder realizar la consolidación de Vuelos y Pasajeros, se cambió el nombre de la columna Cve_Cliente por ID_Pasajero del DataFrame Vuelos y se realizó un inner join, ya que solo se desea tener la información existente entre el pasajero y el vuelo.

##### 3. Ahora se requiere que los datos consolidados de los vuelos y pasajeros se puedan unir con los datos de las Líneas Aéreas. En el caso de que la línea aérea no se pueda relacionar con la de vuelos y pasajeros se deberá indicar que se trata de “Otra” y finalmente se deberá dejar únicamente las columnas:

- Fecha del viaje
- Clase
- Precio
- Ruta
- Edad
- Línea Aérea

##### En esta parte deberás indicar:
- ¿Qué tipo de proceso consideraste para unir los datos que se piden?
- ¿Qué columnas utilizaste para lograr esa relación?
- ¿Qué tipo de unión utilizaste para unir los datos?
- ¿Qué tipo de proceso utilizaste para dejar únicamente las columnas que se piden?

> Para poder consolidar Vuelos y Pasajeros con Líneas Aéreas, se cambió el nombre de la columna Code por Cve_LA y se realizó un left join ya que se necesita información referente a los vuelos sin importar que la información de aerolineas quede vacía. Para solo tener las columnas que se piden, se realizó un DataFrame extra indicando las columnas. No se procedió a eliminar columnas para no perder información.

