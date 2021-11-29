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


## Correr XNAT en una máquina virtual
1. Descargar virtual box
2. Descargar vagrant 
[vagrantfile](https://github.com/luisam19/PDI/blob/main/Vagrantfile) 

**Nota:** Se utilizaron puertos especificos debido a las especificaciones que solicitaba. En caso de tener un puerto que ya este escuchando deshabilitar. 

<img src= "images/464d6c9bca004404719b629b00956e71aa578f4a88d28f8eeeb68a3af001b444.png">  


3. Correr en la ruta donde tiene el vagrantfile las siguientes líneas: 
 ```js 
 vagrant up 
 js Vagrant ssh 
 ```
4. instalar docker en ubuntu
seguir los pasos: <https://docs.docker.com/engine/install/ubuntu/>
5. Instalar docker compose
seguir los pasos: <https://docs.docker.com/compose/install/>
6. Página de la memoria
Seguir los pasos:  <https://phoenixnap.com/kb/docker-memory-and-cpu-limit>
7. Instalar gradle
```js
sudo apt install gradle
```
8. correr los primeros pasos de la guía de la instalación Aura 
```js
// clonar repositorio
$ git clone https://github.com/NrgXnat/xnat-docker-compose 
$ cd xnat-docker-compose
$ git checkout features/dependency-mgmt
// Crear copia de archivo de configuración
$ cp default.env myProps.env
$ ./gradlew composeBuild composeUp
$ ./gradlew composeDown //Recomendación: siempre bajar los servicios 
// Lanzar especificando entorno y archivo de manifiesto
$ ./gradlew -PenvFile=myProps.env -Pmanifest=manifest-1.8.2.json fullStackComposeBuild fullStackComposeUp
```
9. 
```js 
sudo docker-compose up -d 
```
10. 1. Añadir plugin DRQ ->ir hasta plugins 
```js
sudo wget https://bitbucket.org/xnatdev/dicom-query-retrieve/downloads/dicom-query-retrieve-1.0.1-xpl.jar
```
11. Dirigirse al `localhost` en el servidor que este usando 

**user:** admin
**password:** admin

**Configurar los receptores DICOM SCP**
- Ir a Administer/Site Administration/DICOM SCP Receivers
- Clic en New DICOM SCP Receiver
- Ingresar la siguiente información: 
AE Title: XDQR
Port: 8104
Custom Processing: Enabled
Identifier: dqrObjectIdentifier 
- Clic en New DICOM SCP Receiver para crear otro receptor
- Ingresar la siguiente información: 
AE Title: XNAT
Port: 8144
Custom Processing: Disabled
Identifier: dicomObjectIdentifier (Default)
**Configurar nodo DICOM para ORTHANC**
- Ir a Administer/Plugin Settings/DRQ Settings
- Clic en Add New DICOM AE
- Ingresar la siguiente información: 
AE Title: ORTHANC
Host: IP
Label: ORTHANC
Port: 4242
Queryable: yes
Default Q/R AE: yes
Storable: yes
Default Storage AE: yes
- Clic en ping para verificar la conexión




