# Segmentación y operaciones morfológicas 

Fecha: 20 de enero 2022
Autor: Luisa María Zapata Saldarriaga 

# Segmentación
La segmentación de imágenes médicas es el proceso de **detección automática** o semiautomática de límites dentro de una imagen 2D o 3D. Los límites van a representar la imagen de interés. 


<center>

**Segmentación de tumor cerebral**
<img src="images/37d6d1134d4c73e770b0aafa1b0a726348b624ce296b8478b3206382d3e4cef2.png">

</center>

Las imágenes médicas presentan alta variabilidad debido a:
* Anatomía humana
* Métodos de adquisición (rayos X, CT,MRI,PET,SPECT, endoscopia, entre otros)

El resultado de la segmentación se puede utilizar para obtener más información de **diagnóstico**. 

## Aplicaciones
Segmentación de riñones para detección de tumores utilizando redes neuronales convolucionales y deep learning.

<center>

**Detección de tumores utilizando redes neuronales- deep learning**
<img src="images/8e7f6afbc055b8cccbe35c43cb08f88cbc10e5fff2321a52d566f9b64930e925.png">
</center>  


Comparación de la predicción vs Ground truth. True label es lo que se acepta por la comunidad científica para identificar que es un tumor. Disminuir tiempos de segmentación manual, quita mucho tiempo, es importante para no depende de una persona. 

**Detección y clasificación de lesiones en mamografía con deep learning**

Imágenes de mamografía especializada tomosíntesis. Lo hace un algoritmo muy avanzado basado en aprendizaje profundo. 
<center>
<img src="images/4ef4ce726c0411febee79eae544199ec6eae14498cb1f7a0318412231919e39f.png">
</center>

**Qmenta**
Empresa que entrega reportes volumétricos o medidas de regiones cerebral.

Identifica regiones sub-corticales y reporta el volumen de las regiones y lo compara con valores de referencia. 

<center>
<img src="images/385940a833a46360edf9835368c3ca7686c68d40d87f350b524b01cb7a5ec4f5.png">
</center>

**Sub-proceso en flujo de procesamiento**
<center>
<img src="images/eab4e940e26b72fde9a9d73387f56d4b2a20d37c18bbd8dd9996fe27b3e7e8cb.png">
</center>

## Métodos
1. Métodos convencionales o entrada manual, son pocos flexibles

<center>
<img src="images/53d8107a5e095d59b686ea3edb7ee46566da1e07e7124d4cf401fdc66d907a3a.png">
</center>  

2. Métodos suaves, es un enfoque moderno basado en la idea de la aproximación, la incertidumbre y la flexibilidad. 

<center>
<img src="images/6c37fa837d533fdeeee3c3677b9bbfbd731cda01cf789581b912c7483a3e7850.png">
</center> 

3. **Métodos basados en modelos**:
Requieren un contorno o forma inicial que posteriormente se actualiza mediante iteraciones a a la forma final esperada de la forma aproximada (2D o 3D)

a. **Modelo de contornos activos**: es un método extenso, nace de un método activo de serpiente puede definirse conceptualmente como una curva elástica que evoluciona desde su forma y posición inicial como resultado de la acción combinada de fuerzas externas e internas. 

* Definición de la curva que representa el contorno activo x,y coordenadas de función.

El contorno final depende de la búsqueda, de poder obtener minización de la función energía para evitar que se salga del contorno del interés para que permanezca estable en los límites. 

Ejemplo: 
1. Edge-based active contour model using an inflation/deflation force with a damping coefficient (EM)
2. Selective binary and gaussian filtering regularized level set (SBGFRLS)
3. distance regularized level set evolution 

El primero es un método muy bueno y el segundo también. 

<center>
<img src="images/5436509b245268b3bd97b75ec64caf8fbb957ae2afd8dcfd9f398e54cf79c8c8.png">
</center>  

Al encontrar un cambio de energía evita que salga del contorno, y evita que salga 

b. **Umbralización**
Los píxeles individuales en uma imagen se marcan como píxeles de objeto si su valor es mayor que algún valor de umbral y como píxeles de fondo en caso contrario. 

Describe la presencia de uno o varios objetos, se selecciona un línea tipo umbral que nos separe. Estos objetos se clasifican los pixeles que correponden a cada intensidad correspondiente.  la varianza sea la mínima, comparando entre píxeles para diferenciar las clases. 

c. **Umbralización por el método de Otsu**
Para dos clases,una para los píxeles del primer plano y otra para los pixeles en segundo plano.

Se busca crear una mascara binaria para asociar los píxeles para una clase en especifico. Usando la mascara al utilizar una operación, se puede obtener la segmentación entre la imagen inicial y la máscara. Es un método automático. 

d. **Crecimiento de regiones/crecimiento de semillas**

Parte de una semilla. Es una técnica secuencial que inicia con la definción de píxeles semilla para incrementar el tamaño de regiones.
Si se tiene la matriz de intensidades de una imagen y definimos una semilla, se compara los vecinos para encontrar l. Se detiene cuando ya no se tiene similitud.

e. **Médotos de machine learning**
Modelos de aprendizaje automático.

d. Métodos hibridos
Los métodos híbridos combian diferentes 

## Operaciones morfológicas 
Permiten realizar cuatro operaciones básicas:
* Erosión 
* Dilatación
* Cierre
* 

1. Erosión
Para una imagen I y vecindario H, la operación se representa como I /theta H
Consiste en la eliminación de todos los pixels del objeto en cuyo vecindario haya al menos un píxel que pertenezca al fondo. Evaluá que tantos vecinos no son de su clase y lo elimina. 

2. Dilatación
Ampliar la zona del objeto. No logra abarcar toda la región de interés, Se usa para cerrar agujeros. 

3. Apertura
Consiste en la ejecución de una erosión seguida de una dilatación. Se utiliza para eliminar elementos salientes, es decir, suavizar los contornos de un objeto. 
Esta representada por: 

4. Cierre
Consiste en la ejecución de una dilatación seguida de una erosión. Se utiliza para rellenar agujeros.

<center>
<img src="images/fb254d71310c952d9fae6dc82a1e0471d54e648a87a43514b2db7d60798c79ce.png">
</center>  

## Ejemplo práctico
Dataset 1

