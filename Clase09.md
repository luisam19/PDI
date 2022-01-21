# FILTRADO

El filtrado es una operación que cambia la calidad de la imagen en términos de resolución, contraste y artefactos. 

Típicamente el proceso de filtrado involucra aplicar una operación. 

## Filtro de mediana: 
Filtro simple que consiste en reemplazar cada pixel de una imagen por la mediana de la vecindad (NxN) alrededor del píxel. La salida del filtro será una imagen con apariencia más suavizada y menos ruidosa que la imagen de entrada.

## Filtro Gaussiano

<img src ="images/2c6d19f789039699dfd14ded9723dde953ba0bbee8e220456befa8c6fc4a23b6.png">

No es el mejor para filtrar bordes, dado que se pierde información. 

<img src ="images/82b4de3ba462e7377d6b7bf7efd77fb93b1ef0b5f098a477d35b1e89d2b2c1ad.png">  

## Filtro de difusión anisotrópica
Los métodos de difusión anisotrópica están formulados para preservar los bordes ya que permite la eliminación.

Es un método que ha mostrado eficacia en imágenes MRI, conserva los bordes. 

Suele utilizarse en dos aplicaciones:
1. Reducción de ruido como paso de pre-procesamiento para segmentación.
2. Paso de pre-procesamiento para reconstrucción volumétrica, permite obtener reconstrucciones volumétrica más limpias. 

Se conserva los bordes sin embargo se puede perder información relacionada en diferentes tejidos, no se recomienda aumentar mucho la conductancia ni el número de iteraciones. 

Para reconstrucción volumétrica, es más complejo visualizar los vasos y delimitar los bordes por eso es importante quitar los puntos. El realce de bordes es importante para la segmentación. 

<img src ="images/8d719620f013e0b678f8025911ab62c4bd8feed1b8aaa0baeacd4e91dcc93c72.png">

# Registro

Encontrar los parámetros óptimos de una transformación geométrica para alinear espacialmente dos imágenes diferentes del mismo objeto. 

Establece correspondencia espacial entre los píxeles de la imagen móvil con los de la imagen de referencia. 

* i y j son las imágenes de referencia y móvil respectivamente.
* i(x,y) y j(u,v) representan los valores de intensidad de los píxeles ubicados en dos mallas regulares en los espacios de imágen i y j respectivamente.
* Para el mismo sujeto, el mismo punto anatómico z puede estar en la posición x,y y u,v en j. 

<img src ="images/576e69f09ed58000af4e4e8ef88d05a56c7d4dfc70d707603ae39589986730f8.png> 

<img src ="images/2bec82ec6d5d5e52822b23c09f18a28be826042b367e352a681e0b04bbfa0d18.png>

Se aplica una transformación para que coincida con el espacio.

<img src ="images/4178c9cd4ef6c2987b14e4191fd5e2668cccff83251f0c903c15d13267d4e99b.png> 

Posterior al registro, se encuentran en el mismo espacio. 

## Componentes del registro de imágenes:
* *Dimensionalidad*: 2D/2D, 3D/3D, 2D/3D.
* *Transformación*: lineal, no-lineal.
* *Medida de similitud*: intensidades, puntos de referencia, bordes, superficies.
* *Procedimiento de optimización*.
* *Enfoque*: intra-sujeto, inter-sujeto, construcción de atlas. 

## Tipo de registro
<img src ="images/7af7d5c1c3db00584fb7d3129a75807bd4ad2157d8dd9368995f01b50ab82c05.png">  


### 1. Transformación rígida:
Una imagen 3D tiene 6 grados de libertad:
* 3 translaciones
* 3 rotaciones

**Rotación en x**
<img src ="images/3823233ebcc492db76b179211630a92812711d4402f3b418634f19d3f7b72990.png">  

**Rotación en y**

<img src ="images/6db9e9d416099dc18b9dd3be440a063a4d2b3d65be2b722967074d6c490cac02.png">  

### 2. Transformación afín
Una imagen 3D tiene 12 grados de libertad:
* 3 traslaciones
* 3 rotaciones
* 3 escalados
* 3 skew

<img src ="images/23d292559c34ba1c68ca1be9b0592139e930dd72f35c2a20e0f79b28e93a170d.png"> 

# Aplicaciones

Imágenes médicas contienen información anatómica y funcional que puede correlacionarse con patologías. 

La imágenes dinámicas contienen variaciones espaciales que deben ser corregidas para obtener métricas más confiables. 

<img src ="images/0d3ac3538e2c9abd87f686ec4f53af6bdcce602e45be2ad8d94b17591e4135ee.png">

* Comparar dos o más imágenes de la misma modalidad.
* Combinar información de varias modalidades del mismo sujeto.
* Estudios longitudinales, monitorear cambios en el tiempo.
* Relacionar imágenes pre y post-operatorias luego de cirugía. 

Ejemplos:
<img src ="images/388e61ffec5a6cd76731dfed7c2dd58c6040c9bdaecbd59b57ad2d9251b243f1.png">

* Corrección de movimiento probablemente durante la adquisición

<img src ="images/2f0a1046dfa4acb482e66b8fc33b07abc52b601e53fefc7ef16dd302ef50ecca.png"> 

* Imágenes dinámicas
Durante un largo periodo de tiempo se adquieren cortes de una zona especifica del cuerpo, se obtiene información del contraste.

<img src ="images/6d3e12fac7eae895e4acbcc46c885747a105d0b4c1203bb28785de78ddef92ce.png>  

