# CIFF 2016 - PROYECTO DE GRUPO – AF#5

### Innovando el Desarrollo de Modelos a través del Big Data.

A continuación se detallará el contenido y uso del paquete prusontchm generado para python 2.7.

## Instalación

Para realizar la instalación bastará con ejecutar en la consola de comandos el siguiente código:

```javascript
python -m pip intall prusontchm
````

## Contenido

Una vez instalado el nuevo paquete, se prodrá hacer uso de las distintas funcionalidades de que dispone, a continuación se detallan:

* A.1) Limpieza automatizada de datos. Donde se identifican los valores y / o filas no válidas y se resuelve automáticamente el problema. Los valores NaN son sustituidos por la mediana de la variable, y los valores fuera de rango son sustituidos también por la mediana si se trata de valores numéricos o por la moda en otro caso.

Para poder hacer uso de esta función sólo es necesario importar la librería DataCleaning de nuestro paquete. Se puede importar ejecutando el siguiente comando:

```javascript
from prusontchm import DataCleaning as dc
````

Y posteriormente llamar a la función limpiezaDeDatos cuyo parámetro de entrada será el Data Frame que se desee limpiar y se devolverá el Data Frame limpio.

```javascript
dfLimpio = dc.limpiezaDeDatos(df)
```

* A.4) Creación automática de ratio y selección de los mejores ratios utilizando Principal Component Analysis y árbol de decisión.

Para la creación de nuevos ratios se ha creado la función NuevosRatios de en la librería ratios. Que dado un Data Frame genera los siguientes nuevos ratios para todas sus columnas a excepción de las variables target e id. 

(X-Y)/Y

 X+Y
 
X*Y

 X/Y
 
 X-Y
 
 X^2
 
 Se importa mediante el comando:
```javascript
from prusontchm import ratios
```

Y al ejecutar 
```javascript
df = ratios.NuevosRatios(df)
```
Obtenemos un nuevo Data Frame con las variables originales y las nuevas.

También se ha generado un método que utilizando PCA y árbol de decisión seleccione los 30 mejores ratios, este es Seleccion_Ratios de la nueva librería RatioSelection

```javascript
from prusontchm import RatioSelection as rs
rs.Seleccion_Ratios(df)
```
Este método tiene de entrada un Data Frame con todos las variables que se desee tener en cuenta y devuelve el ranking de las 30 mejores por orden de feature_importances, este dato también se incluye en la salida del método.

* A.6) Comparar y elegir el métodos (LR, DT, RF, NN, etc..., por lo menos 5 métodos) que mejor seaplique a los datos de forma automática y supervisada.

Por último se ha creado un método para elegir el mejor modelo para un cojunto de datos dado. Esta función realiza una comparación por tiempo y gini de los métodos Generalized Linear Model (GML), Logistic Regression, Random Forest, Decision Tree (DT) y Support Vector Machine (SVM).

Para poder ejecutarlo basta con importarse la librería y realizar la llamada con el Data Frame sobre el que se desee implementar el modelo:
```javascript
from prusontchm import modelSelection as ms
ms.eleccionmodelo (df)
```
Devolverá por pantalla los métodos en orden de velocidad y gini ordenados de mejor a peor.

## Licencia

El código aquí contenido esta bajo la licencia del MIT.

## Proyecto realizado por

César Hernández Martín

Sara Otero de Navascués Tomé