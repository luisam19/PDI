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

1. **Métodos convencionales** `Hard computing` o entrada manual, son pocos flexibles

<center>
<img src="images/53d8107a5e095d59b686ea3edb7ee46566da1e07e7124d4cf401fdc66d907a3a.png">
</center>  

2. **Métodos suaves** `Soft computing`, es un enfoque moderno basado en la idea de la aproximación, la incertidumbre y la flexibilidad. Son muy buenos para segmentación con redes de convolucionales.  

<center>
<img src="images/6c37fa837d533fdeeee3c3677b9bbfbd731cda01cf789581b912c7483a3e7850.png">
</center> 

3. **Métodos basados en modelos**:

Requieren un contorno o forma inicial que posteriormente se actualiza mediante iteraciones a a la forma final esperada de la forma aproximada (2D o 3D) o bordes aproximados.

Las actualizaciones se realizan con base a un conocimiento definido a priori sobre como estos métodos determinan los bordes probables de los objetos. 

a. **Modelo de contornos activos**: 

Es un método extenso, nace de un método activo de serpiente puede definirse conceptualmente como una curva elástica que evoluciona desde su forma y posición inicial como resultado de la acción combinada de fuerzas externas e internas. 

* Definición de la curva que representa el contorno activo `x,y` coordenadas de función, `s` espacio paramétrico.

<center>
<img src="images/8a4938684744af687176a52e724dcce0eb1c0d180eb970ec3b0d624a11f4da43.png">
</center>

* Función asociada a la forma del contorno sujeto a una imagen. `E: energía`

<center>
<img src="images/0320b6d4c818848707a8b441ed22845999889727e642a1e7531ec27fb6bbe747.png">
</center>

El contorno final depende de la búsqueda, de poder obtener minimización de la función energía para evitar que se salga del contorno del interés para que permanezca estable en los límites. 

Dependiendo de su ubicación, afectará como se configuran las ecuaciones de energía. El problema de encontrar el límite del objeto es un problema de minimización de energía. 

**Ejemplo:** 
1. Manual realizada por médico experto.
<center>
<img src="images/cdb2bd20b323f91939bb48d9c4fe5492bd922045b8764a3bd5f45805e3caaa87.png">

<img src="images/5e501ebc1546d85fa6df0781adfaacb1bd7f77491b9ea722819af171a16a1936.png">

</center> 

2. Edge-based active contour model using an inflation/deflation force with a damping coefficient (EM).
<center>
<img src="images/b1a9ef2efd3b3c741c9d4f03c4f64c0a5df0832205370b0c94bdc91461562ff0.png"> 

<img src="images/769dd0fcc727f15fbe2bde3dfa3e327aa862c5a98658332428df3d938f84591d.png"> 

</center>

3. Selective binary and gaussian filtering regularized level set (SBGFRLS).
<center>
<img src="images/78319e0df1540b85c286246eb53b5d7fc3396ae8eaba7d138f6232c89628a31b.png">

<img src="images/6661a493e3cb9ebd7779026cb2ee7a56645609dfddf2535e44445cd1ffd01db1.png"> 

</center>

4. distance regularized level set evolution 

<center>
<img src="images/c15a1824b741d66720273bf5edd65163425118dc8c26595771fbdc541ca079c7.png">

<img src="images/b6230cc7f7138618d94828f702cd5b8c52b93fdd6415c9fdbea470fa5b2a5342.png"> 

</center>

El primero es un método muy bueno y el segundo también.Sim embargo el tercer  método toma información que no corresponde a la región y el cuarto no toma toda la información. 

Al encontrar un cambio de energía evita que salga del contorno, y evita que salga 


4. **Métodos basados en regiones:**

a. **Umbralización**

Los píxeles individuales en uma imagen se marcan como píxeles de `objeto` si su valor es mayor que algún valor de umbral y como píxeles de `fondo` en caso contrario. 

Describe la presencia de uno o varios objetos, se selecciona un línea tipo umbral que nos separe. Estos objetos se clasifican los pixeles que corresponden a cada intensidad correspondiente.  la varianza sea la mínima, comparando entre píxeles para diferenciar las clases. 

<center>
<img src="images/18d37b1a0b4c592facb1bea39a0bbee5b60d2f6eb30a047b26ee7ea6fd65056f.png">  
</center>


b. **Umbralización por el método de Otsu**
Para dos clases,una para los píxeles del primer plano y otra para los pixeles en segundo plano, el método utiliza la varianza para minimizar entre los píxeles de la misma clase y maximizarla entre píxeles de clase diferente.

Se busca crear una mascara binaria para asociar los píxeles para una clase en especifico. Usando la mascara al utilizar una operación, se puede obtener la segmentación entre la imagen inicial y la máscara binaria, se asocia los píxeles con una clase en especifico. Es un método automático. 

<center>
<img src="images/42ad97fc4d4675ca0435f93bb6b7187574e099842987104162571f5838e83254.png"> 
</center>

El método busca el umbral que asegura las dos clases y que tenga una mínima varianza. 

c. **Crecimiento de regiones/crecimiento de semillas**

Parte de una semilla. Es una técnica secuencial que inicia con la definición de píxeles semilla para incrementar el tamaño de regiones.
Si se tiene la matriz de intensidades de una imagen y definimos una semilla, se compara los vecinos para encontrar l. Se detiene cuando ya no se tiene similitud.

<center>
<img src="images/78854b9c1b48dbfb1702a06bfb3ec5caafb6f82e6c3120589d0180925b1045b2.png">
</center>

5. **Médotos de machine learning**

Modelos de aprendizaje automático, permiten identificar patrones complejos a partir de imágenes,el reconocimiento o distinción de características permiten la segmentación. 

6. **Métodos híbridos**
Los métodos híbridos combinan diferentes técnicas que pueden provenir de varios grupos y categorías de métodos utilizados en la segmentación.  

___________________________________________________

# Operaciones morfológicas 

Los operadores morfológicos permiten manipular la forma de las imágenes. 

Permiten realizar cuatro operaciones básicas:
* Erosión 
* Dilatación
* Cierre
* Apertura

1. **Erosión**

Para una imagen `I` y vecindario `H`, la operación se representa como `I /theta H`.

Consiste en la eliminación de todos los pixels del objeto en cuyo vecindario haya al menos un píxel que pertenezca al fondo. **Evaluá que tantos vecinos no son de su clase y lo elimina**. 

<center>
<img src="images/c95da05ab28851170a059a45bd1ea5b20d830ea5ea03f4b92ae2ee69e142e066.png">  
</center>

2. **Dilatación**

Ampliar la zona del objeto. No logra abarcar toda la región de interés, Se usa para **cerrar agujeros pequeños**. 

<center>
<img src="images/38c2605b59af85a9454a4d3352fde59effd4740f6aa59fdae4800ccfad530151.png">
</center>

3. **Apertura**
Consiste en la ejecución de una erosión seguida de una dilatación. Se utiliza para eliminar elementos salientes, es decir, suavizar los contornos de un objeto. 

Esta representada por: 

<center>
<img src="images/8ebc6053cb7424ba8807e4cde81f428303be7249944a27be27435408f102b3c9.png">  
</center>

4. **Cierre**
Consiste en la ejecución de una dilatación seguida de una erosión. Se utiliza para **rellenar agujeros pequeños sin alterar el tamaño del objeto** o suavizar el contorno.

Esta representada por: 

<center>
<img src="images/bf87a97b89e7decfa6a9c4235f953c0c4051bd8368320be26f233096d8c9131a.png"> 
</center>

Primero dilatamos y luego erosionamos. 

<center>
<img src="images/fb254d71310c952d9fae6dc82a1e0471d54e648a87a43514b2db7d60798c79ce.png">
</center>  

___________________________________________________

## Ejemplo práctico en Slicer

[Dataset 1]()

Imagen CT de los pulmones

* Usar la herramienta Segment Editor de Slicer
* Utilizar el método de crecimiento a partir de semillas

Segmentar 3 tejidos:
* Pulmones
* Vías aéreas
* Otros tejidos

[Dataset 2]()

Imagen CT de los riñones

* Usar la herramienta Robust Statistic Segmenter

- Approximate volume: 150 ml,
- Intensity homogeneity: 0.7,
- Boundary smoothness: 0.4

