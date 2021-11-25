# XNAT

Fecha: 23 Noviembre 2021 
## ¿Qué es XNAT?

* Plataforma de software de informática médica de código abierto
* Orientada a la ejecución de investigación con imágenes médicas
* Importar, almacenar, procesar y distribuir imágenes y otro tipo de información del estudio de manera segura. 

![picture 1](images/ac782247633dfa43b26d65b0c558ec2d528db199c66d13201abd01bb8e04856a.png)  

### Componentes de XNAT
![picture 2](images/72a50d5d587196744824e66bfdb5477aa8505feed84e49ac31fb86696389363d.png)  

* Busqueda y exploración de grandes datasets. Permite almacenar, navegar y consultar datos

* Ejecutar procesamiento complejo en los datos usando computación avanzada
* Incluye iun motor de pipelines para programación de flujos de trabajo complejos conmúltiples niveles de automatización 

### DICOM SCP Receiver

Una ocpión para enviar datos desde un scanner a XNAT

![picture 3](images/e9c7e9335cc8a1aa7ac18b17c39c681af95c319dfb00e66bff89e7d591a3469a.png)  

Se le vincula un proyecto, es como una carpeta temporal, y se redirige a los proyectos propios. 

![picture 4](images/85c155c27e77851782aca56ac1f2c794ee4f2a2ef70beba7ef934ca622af5f7e.png)  

### Plugins

Son usados por XNAT com ouna manera de extender su funcionalidad.

Cada plugin está empaquetado en su propio contenedor que puede ser implementado de forma separada y distinta de la aplicación principal

### Container server

* Permite ejecutar aplicaciones desarrolladas fuera de XNAT. 
* Se pueden asociar por medio de docker Hub.
* Se pueden definir los comandos para ejecución del contenedor en la plataforma XNAT



