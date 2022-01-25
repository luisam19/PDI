# FILTRADO Y REGISTRO DE IMÁGENES

# Filtrado
## 1. Definición: 

El filtrado es una operación que cambia la calidad de la imagen en términos de resolución, contraste y artefactos. 

Típicamente el proceso de filtrado involucra aplicar una operación matemática a cada píxel de la imagen.

El filtrado espacial modifica la intensidad de cada píxel de una imagen utilizando una función que opera sobre los píxeles vecinos.  

Ej: Mejorar la resolución cuando se le aplica un filtro. 

<center>
<img src ="images/7a0adea0addd18cb1b92550ddf784ea3b0f9bb45fbc2290fc2c44410544d85a7.png">  

<img src ="images/9486c4d82a3c3649ca0f769d6f620f62472682c29dc088265f0df1122f11a8b7.png"> 
</center>

## TIPOS DE FILTROS: 

## Filtro de mediana: 
Filtro simple que consiste en reemplazar cada pixel de una imagen por la mediana de la vecindad (NxN) alrededor del píxel. La salida del filtro será una imagen con apariencia más suavizada y menos ruidosa que la imagen de entrada. 

<center>

<img src ="images/9bb5957644c3359605a7794b374094420aaaa38a4d43bbe12d922dab84c72fd6.png"> 

<img src ="images/456262128caf78d2572a8ca843e0a28c95f5e58f1e9238661c13c742dd0cfa1d.png">  
</center>

###  Ejemplo en slicer de filtro de mediana
1. Cargar imágenes de [dataset 1]()

**Imagen sin filtrar**
<center>
<img src ="images/d452f50d5616c3d3cebb86c9bd9d74b32bba2e86c115c80816badb58994c4065.png">
</center>

2. Seleccionar módulo Volume Rendering

    ```Modules-> Filtering -> Denoising -> Median Image filter```

3. Definir el tamaño del filtro
<center>
<img src ="images/dabee58d0c5facbb36c8f4194ccab84703a30c3634c57b2d5b3121c49b4a6dd4.png">  
</center>

<center>

**Imagen filtrada**

<img src ="images/9d4b9f1d15801974bfc987ceadf303f7acf1b1a2fcf8bcca6c6d3b34107d8c0b.png">
</center>

4. Seleccionar la imagen de entrada
5. Asignar nombre a imagen de salida 

## Filtro Gaussiano

<center>
<img src ="images/2c6d19f789039699dfd14ded9723dde953ba0bbee8e220456befa8c6fc4a23b6.png">
</center>

Es muy utilizado, en donde decrece en los extremos. Se especifica un tamaño de aplicación que va determinar el ancho del filtro ya sea en píxeles o voxeles dependiendo de las dimensiones de la imagen. 

A medida que se aumenta el tamaño se puede perder información.A mayor ancho suavizado de la imagen. 

No es el mejor para filtrar bordes, dado que se pierde detalles de los bordes es decir se pierde información a medida que se eliminan los artefactos. 

<center>
<img src ="images/82b4de3ba462e7377d6b7bf7efd77fb93b1ef0b5f098a477d35b1e89d2b2c1ad.png">  
</center>

## Filtro de difusión anisotrópica

Los métodos de difusión anisotrópica están formulados para **preservar los bordes** ya que permite la eliminación Y **Elimina artefactos de punto** más conocidos como *sal y pimienta*. Es un métodos basado en la aproximación de derivadas parciales mediante diferencias finitas. 

Es un método que ha mostrado eficacia en imágenes MRI en T1 y T2, conserva los bordes. Puede usarse en otras modalidades, pero muestra buenos resultados al trabajarlo sobre imágenes de MRI. 

Suele utilizarse en dos aplicaciones principalmente:
1. Reducción de ruido como paso de pre-procesamiento para segmentación.
2. Paso de pre-procesamiento para reconstrucción volumétrica, permite obtener reconstrucciones volumétrica más limpias. 

Se conserva los bordes sin embargo se puede perder información relacionada en diferentes tejidos, no se recomienda aumentar mucho la **conductancia** ni el **número de iteraciones**. 

Para reconstrucción volumétrica, es más complejo visualizar los vasos y delimitar los bordes por eso es importante quitar los puntos. El realce de bordes es importante para la segmentación. 

<center>

**Imagen de RM original**

<img src ="images/ee1edbee75b7e5cdf3756c6b618cd67265d4939ab6c980e8713a19ef77200bd9.png"> 

**Imagen de RM filtrada con conductance=1 y 5 iteraciones**

<img src ="images/a4f370740682c5f238622797555d36f64f02956c9e6e1113412149a7adba2a21.png"> 

**Reconstrucción volumétrica**

<img src ="images/8d719620f013e0b678f8025911ab62c4bd8feed1b8aaa0baeacd4e91dcc93c72.png">
</center>

###  Ejemplo en slicer de filtro de
1. Cargar imágenes de (dataset1)[]
2. Seleccionar modulo de gradiente

    ```-> module->filtering->denoising-> Gradient Anisotropic Diffusion```
3. Definir parámetro conductance: Menor valor de conductividad permite preservar más los bordes y obtener menos suavizado. 
4. Definir número de iteraciones: El número de iteraciones controla la cantidad de suavizado que se realiza dentro de las regiones limitadas por los bordes. 
5. Definir Time step: Depende de la dimensionalidad de la imagen. Para imágenes 3D se recomienda utilizar el valor por defecto. 
6. Seleccionar imagen de entrada
7. Asignar nombre a imagen de salida.

**Imagen filtrada**
<center>
<img src ="images/c42055ac77d19511803d112de8708fcc734c8f76c60b4eaf62e9fb8a527a5585.png">  
</center>
Se suavizo más el tejido. 

___________________________________________________

# Registro

Encontrar los **parámetros óptimos** de una transformación geométrica para **alinear** espacialmente dos imágenes diferentes del mismo objeto. 

Establece correspondencia espacial entre los píxeles de la **imagen móvil** con los de la **imagen de referencia**. 

* i y j son las imágenes de referencia y móvil respectivamente.
* i(x,y) y j(u,v) representan los valores de intensidad de los píxeles ubicados en dos mallas regulares en los espacios de imagen i y j respectivamente.
* Para el mismo sujeto, el mismo punto anatómico z puede estar en la posición x,y y u,v en j. 

<center>
<img src ="images/576e69f09ed58000af4e4e8ef88d05a56c7d4dfc70d707603ae39589986730f8.png"> 

<img src ="images/2bec82ec6d5d5e52822b23c09f18a28be826042b367e352a681e0b04bbfa0d18.png">
</center>

Se aplica una transformación para que coincida con el espacio.

<center>

<img src ="images/4178c9cd4ef6c2987b14e4191fd5e2668cccff83251f0c903c15d13267d4e99b.png"> 
</center>

Posterior al registro, se encuentran en el mismo espacio. 

## Componentes del registro de imágenes:
* *Dimensionalidad*: 2D/2D, 3D/3D, 2D/3D (poco comunes).
* *Transformación*: lineal, no-lineal.
* *Medida de similitud*: intensidades, puntos de referencia, bordes, superficies.
* *Procedimiento de optimización*.
* *Enfoque*: intra-sujeto (para un diagnostico se suele usar varias imágenes), inter-sujeto, construcción de atlas. 

## Tipo de registro
<img src ="images/7af7d5c1c3db00584fb7d3129a75807bd4ad2157d8dd9368995f01b50ab82c05.png">  
Lo más importante es la naturaleza de la transformación puede ser:

* Rígida
* Afín
* Curva
* Proyectiva


### 1. Transformación rígida:
Una imagen 3D tiene 6 grados de libertad:
* 3 traslaciones
* 3 rotaciones

**Matriz de transformación traslación**
<img src ="images/5b77dc54f96c84c18bc78952bf14124b74aa25c4d3b3455fcc68ff72eb9fd1a3.png">

**Rotación en x**
<img src ="images/3823233ebcc492db76b179211630a92812711d4402f3b418634f19d3f7b72990.png">  

**Rotación en y**

<img src ="images/6db9e9d416099dc18b9dd3be440a063a4d2b3d65be2b722967074d6c490cac02.png">  

### 2. Transformación afín
Una imagen 3D tiene 12 grados de libertad:
* 3 traslaciones
* 3 rotaciones
* 3 escalados
* 3 skew (inclinar una imagen basada en paralelismo)
<center>
<img src ="images/23d292559c34ba1c68ca1be9b0592139e930dd72f35c2a20e0f79b28e93a170d.png"> 
</center>

# Aplicaciones

Imágenes médicas contienen información anatómica y funcional que puede correlacionarse con patologías, es necesario hacer una operación de registro porque es llevar información a otro espacio. Ayuda a sacar conclusiones sobre el estado del paciente.  

La imágenes dinámicas contienen variaciones espaciales que deben ser corregidas para obtener métricas más confiables. 

<center>
<img src ="images/0d3ac3538e2c9abd87f686ec4f53af6bdcce602e45be2ad8d94b17591e4135ee.png">
</center>

* Comparar dos o más imágenes de la misma modalidad.
* Combinar información de varias modalidades del mismo sujeto.
* Estudios longitudinales, monitorear cambios en el tiempo.
* Relacionar imágenes pre y post-operatorias luego de cirugía. 

**Ejemplos:**
<center>
<img src ="images/388e61ffec5a6cd76731dfed7c2dd58c6040c9bdaecbd59b57ad2d9251b243f1.png">
</center>

* Corrección de movimiento probablemente durante la adquisición

<center>
<img src ="images/2f0a1046dfa4acb482e66b8fc33b07abc52b601e53fefc7ef16dd302ef50ecca.png"> 
</center>

No hay correspondencia durante toda la adquisición porque hubo un movimiento del paciente. 

* Imágenes dinámicas
Durante un largo periodo de tiempo se adquieren cortes de una zona especifica del cuerpo, se obtiene información del contraste.

<center>
<img src ="images/6d3e12fac7eae895e4acbcc46c885747a105d0b4c1203bb28785de78ddef92ce.png">  
</center>

**Ejemplo slicer Registro**
Flujo de trabajo 
* Sujeto A
    - Registro afín de la imagen T2w a T1w 
* Sujeto B
    - Registro afín de la imagen T2w a T1w 
* Imágenes T1w
    - Registrar  imagen de Sujeto B a imagen de sujeto A. 

1. Cargar imágenes de dataset 2
2. Cambiar visualización a Four-up
3. Cerrar aros
4. Superponer *SubjectA_T1* sobre *SubjectA_T2* con un umbral 0.6.
5. Seleccionar módulo de registro BRAINS.
6. Definir imagen de referencia e imagen móvil
7. Asignar nombre a archivo con transformación lineal
8. Inicializar la transformación 
9. Seleccionar las fases de registro rígido 6DOF y afín 12DOF. 
10. Ejecutar

Se toma la imagen fija, la de mayor resolución o la que tiene mayor información de interés. 