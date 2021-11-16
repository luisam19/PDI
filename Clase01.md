# Procesamiento de imágenes médica

Área de constante crecimiento por el interés en diagnóstico, tratamiento de enfermedades de forma no invasiva y planeación de intervenciones.

## Contenido
* Principios de adquisición de imágenes médicas
* Procesamiento de imágenes médicas
* Visión por computador
* Neuroimagen 

## Evaluación 
Proyetos o laboratorios por unidad (%17)
Exposiciones que deben incluir coevaluación (8%)
Cada unidad 25% de cada mes 


## Historia
* Empezo con rayos X entre 1845-1923 Wilhelm Conrad Roentgen. No lo patento sino que lo dono a la humanidad. 
* 28/Dic/1985 Rontgen publica su manuscrito- Nobel física 1901
* 1896 49 monografías y 1044 artículos
* 1912 Max von Laue demostró que los rayos X eran ondas EM de longitud de onda corta-> Nobel física 1914
* 1950's primeras aplicaciones de ultrasonido en medicina
* 1969 introducción de unidad especializada de mamografía (aprobada por la FDA en el 2000)
* Hounsfield -Cormack- The beatles 
* 1970's SPECT cerebral
* 1976 Peter Mansfield desarrolla secuencias EPI y avanza en acelerar la formación de imágenes
* 1980 primera imágenes de cabeza
* 1980's primeros acercamimentos al PET (invención completa en 2001)
* 1981 primer resonador instalado en un hospital en Londres

*Las imágenes como datos*

# Bases para el uso de contenedores 

La contenerización implica encapsular o empaquetar el código de software. La contenerización permite agrupar nuestro software junto con todas sus dependencias en un paquete autónomo para que pueda ejecutarse sin pasar por un proceso de configuración problemático. 

Escenario: Usted desarrolló una aplicación para gestión de libros, esta permite almacenar información sobre los libros adquiridos y además tiene un sistema de control de libros prestados para sus amigos. Las dependencias son las siguientes:
- ¿Qué paasa si no se logran instalar las dependencias correctamente? No será posible ejecutar la aplicación

Para evitar este tipo de problemas se uutiliza contenedores. desarrolle y ejecute la aplicaicón dentro de un **entorno aislado** que coincida con su entorno de implementación final.

Coloque su aplicación dentro de un solo archivo (Conocido como imagen) junto con todas sus dependencias y configuraciones de implementación necesarias

## Máquinas virtuales vs Docker
* permite crear contenedores.
#### Las máquinas virtuales
Las máquinas virtuales aísla aplicaciones y asigna recursos al ejecutar la aplicación.
* Se pueden compartir como imágenes. No dependiente del OS del host.
* Se pueden ejecutar simultáneamente por medio de un hipervisor 
#### Docker
Se pueden compartir como imágenes
Se pueden ejecutar varios contenedores simultáneamente.
* Portátil: se puede utilizar con cualquier sistema operativo
* Ligero: Utiliza el sistema operativo del host
* Seguro: sólidas funciones de aislamiento predetermiandas. 

### ¿Por qué usar Docker?
* Desarrollar aplicaciones en cualquier OS
* Fácil de compartir aplicaciones entre equipos
* Fácil de escalar en varios servidores
* Excelente solución para computo en la nube
* Gran comunidad y librerías de imágenes
* Elimina la dependencia de la infraestructura
* Permite a los desarrolladores centrarse en el desarrollo de aplicaciones 







