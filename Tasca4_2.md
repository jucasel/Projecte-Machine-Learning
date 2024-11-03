```python

```

Pel que fa al procés de recol·lecció de dades, hauràs de dissenyar un document amb tota la informació que has après en aquest sprint:

Fonts de dades
Mètodes de Recol·lecció de Dades (inclou tècniques de mostreig si correspon)
Format i Estructura de les Dades
Limitacions de les dades
Consideracions sobre Dades Sensibles

**Documentación del Proceso de Recolección de Datos**


---


***Proyecto: Datos Bancarios “bank dataset.csv”***


---



El proceso de recolección de datos debe seguir un conjunto de fases lo más estándar posible, que permita llevar a cabo de manera automática la mayor parte del proceso.

A continuación se muestra una propuesta de proceso que parte de la identificación inicial de las fuentes y concluye con los procesos de seguimiento y actualización del proceso. Este proceso debe mantener la calidad del dato disponible, sin perder precisión ni integridad.


1. Fuentes

En un caso de empresa bancaria, los datos pueden salir de su propio sistema o de forma específica para obtener esos datos en concreto.

En el caso de datos internos, las bases de datos propias pueden ser la primera y más fiable fuente de obtención, ya que nos permite disponer del historial de todos los clientes del banco, incluso de diversa procedencia si, como en el caso español se han producido adquisiciones, fusiones, etc.
En general, un CRM del propio banco puede ser la fuente principal, especialmente en el caso de información financiera. Y si fuera preciso se pude lanzar una campaña de actualización de datos con los clientes actuales para obtener información de primera mano.

A nivel externo, podemos hablar de obtención de datos a partir de campañas de marketing anteriores o de campañas específicas para este proceso, a través de encuestas, entrevistas, etc.

Sí que sería importante considerar el grado de veracidad de los mismos, dando más trascendencia a los datos propios que a los que se pueden sacar de una campaña externa, y que puede representar una mayor dispersión de los datos obtenidos.


2. Métodos de recolección de datos:

Procedimientos y Herramientas:

Partiendo de dos tipos diferentes de datos, llamados internos y externos, en ambos casos podemos trabajar con un sistema sencillo y transparente, que puede aplicarse a ambas fuentes. Un formato común de archivos CSV puede ser aplicable a los datos disponibles de manera interna como a los obtenidos de manera externa, con formularios con facilidad de captura de la información en un modelo semejante al utilizado de manera interna.

De este modo obtenemos de diferentes fuentes los CSV “bank dataset”, cuya recopilación puede establecerse con la frecuencia que se considere oportuna, ya que, más allá que los datos originales no van a sufrir cambios, las campañas nuevas y de actualización pueden ir llegando de manera asíncrona.


#Proceso De Recolección

import pandas as pd

csv_url = "https://raw.githubusercontent.com/jucasel/Projecte-Machine-Learning/main/bank_dataset.CSV"
df = pd.read_csv(csv_url)

df.head()







3. Formato i Estructura de los Datos

Es importante tener en cuenta que, al tratar con diferentes fuentes de datos, debería realizarse un proceso de normalización y limpieza de Datos, de modo que se estandaricen al máximo los valores que pueden llevar a confusión o diferentes tipos de respuesta. Imaginemos el caso de diferentes representaciones del estado civil, los formatos de fecha, tipos de moneda, etc.

En nuestro caso, el bank dataset CSV, tiene definida la siguiente estructura:

- age, (Feature), Integer
- job, (Feature), Categorical
- marital, (Feature), Categorical
- education, (Feature), Categorical
- default, (Feature), Binary
- balance, (Feature), Integer
- housing, (Feature), Binary
- loan, (Feature), Binary
- contact, (Feature), Categorical
-  day, (Feature), Date
-  month, (Feature), Date
-  duration, (Feature), Integer
-  campaign, (Feature), Integer
-  pdays, (Feature), Integer
-  previous, (Feature), Integer
-  poutcome, (Feature), Categorical
-  deposit (Target), Binary

y como información adicional, vista en https://archive.ics.uci.edu/dataset/222/bank+marketing


- age (numeric)
- job : type of job (categorical: "admin.","unknown","unemployed","management","housemaid","entrepreneur","student", "blue-collar","self-employed","retired","technician","services")
- marital : marital status (categorical: "married","divorced","single"; note: "divorced" means divorced or widowed)
- education (categorical: "unknown","secondary","primary","tertiary")
- default: has credit in default? (binary: "yes","no")
- balance: average yearly balance, in euros (numeric)
- housing: has housing loan? (binary: "yes","no")
- loan: has personal loan? (binary: "yes","no")
* Related with the last contact of the current campaign:
- contact: contact communication type (categorical: "unknown","telephone","cellular")
- day: last contact day of the month (numeric)
- month: last contact month of year (categorical: "jan", "feb", "mar", ..., "nov", "dec")
- duration: last contact duration, in seconds (numeric)
* other attributes:
- campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)
- pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric, -1 means client was not previously contacted)
- previous: number of contacts performed before this campaign and for this client (numeric)
- poutcome: outcome of the previous marketing campaign (categorical: "unknown","other","failure","success")

Output variable (desired target):
- deposit - has the client subscribed a term deposit? (binary: "yes","no")

5. Consideraciones sobre Datos Sensibles

Este dataset contiene datos sensibles en diferentes áreas (personal, financiera…) lo que debe cumplir la reglamentación de protección de datos que aplique, y también importante, que los clientes tengan la seguridad y esten bien informados del correcto tratamiento de los datos.

Los tipos de datos sensibles que se identifican son los siguientes:

1. Datos Personales Sensibles
Age
Job
Marital
Education

2. Datos Financieros Sensibles
Balance
Loan
Housing
Default

En el caso de considerar datos procedentes de campañas, encuestas exteriores deben tenerse en cuenta datos del tipo medio de contacto, fecha de contacto, etc. El historial también debe tenerse en cuenta cara a no mostrar interés del cliente por productos y su comportamiento ante ciertas características de campaña.

Finalmente, no olvidar la variable etiqueta, puesto que saber si se realiza o no depósito también puede dar información de la situación económica de un cliente.

Finalmente, respecto a las medidas de protección, debrán aplicarse medidas del siguiente tipo:

-       Anominizar los datos recibidos.
-       Si es preciso, cifrar los datos.
-       Restringir el acceso a los datos
-       Asegurar el cumplimiento de la normativa de protección de datos.
-       Obtener el consentimiento del cliente para el tratamiento de datos.


