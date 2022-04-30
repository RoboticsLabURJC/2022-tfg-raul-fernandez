# 2022-tfg-raul-fernandez
# Intrucciones de uso del Maestro de Ceremonias

  ### 1. Instalar Selenium
  - Lo primero que necesitamos es descargarnos de su [página](https://www.selenium.dev/documentation/webdriver/getting_started/install_drivers/) los drivers del navegador que nosotros usemos, esto nos dará permiso para poder usar el navegador de manera automática. Es **muy importante** que la versión del driver sea la misma versión que la de nuestro navegador, si no sabes la versión de tu navegador lo puedes ver en esta [página](https://www.whatismybrowser.com/detect/) en el apartado de "Detect web browser".
  
  - Añadir la librería se Selenium en Pycharm, File -> Settings -> Python Interpreter -> pulsamos en el + que aparece en la parte izquierda y ecribimos selenium e instalamos el paquete.
  
  ![image](https://user-images.githubusercontent.com/57095736/165766276-3cfd5959-13e5-4dc8-a823-2157bdb4ca2b.png)
  
   ### 2. Definir directorios
   - Debemos dirigirnos a la carpeta raul(CAMBIAR ESTO) al archivo torneoAutomático.py y en la función init cambiar el valor de la variable *driver_path* y poner el path donde hemos guardado el driver descargado en el apartado anterior.
   
   ![image](https://user-images.githubusercontent.com/57095736/165767461-eedf6616-af8d-4de7-94df-00972d768210.png)
   
   ### 3. Lanzamiento automático contenedores
   **Si no quieres** que los contenedores docker, RADI y servidor se desplieguen y cierren solos dirigite al archivo run.py en la carpeta raul(CAMBIAR ESTO) y comenta las llamadas a los métodos startContainers, launchServer, lanzarRadi y stopContaners (cuidado esta última se llama dos veces). SI USAS LINUX NO LANZES EL SERVIDOR AUTOMÁTICAMENTE ya que el TFG fué desarrollado en Windows y la manera que se usa para detenerlo solo funciona en Windows así que también comenta la función stopServer del run.py. En caso de querer que se lanzen y detengan los contenedores de manerá automática:
   - En la función launchServer debemos poner el path donde se encuentre el archivo manage.py
![image](https://user-images.githubusercontent.com/57095736/165770842-2d2b1e38-48b3-48e2-928f-ac4b9d1b98e1.png)

- El lanzamiento y detención de los contenedores Docker no debería dar problemas ya que se usan comandos Docker en ambos casos.

### 4. Emisión vía twitch
Este paso lo podemos omitir si no estamos interesados en retransmitir vía Twitch.

- Abrir OBS: el primer paso será instalar el programa [OBS](https://obsproject.com/es/download) si no lo tenemos instalado, una vez lo tengamos vamos a la función openObs debemos poner el path donde se encuentra el ACCESO DIRECTO a OBS, esto es un pequeño truco para evitar problemas de seguridad del programa, si no sabes donde se encuentra escribe en el explorador del ordenador OBS y hacemos click derecho en el resultado y abrir ubicación del archivo. También cambia el nombre del acceso directo a obs64 para evitar problemas de espacios, así solo tendrás que cambiar el path indicado en rojo en la foto.

![image](https://user-images.githubusercontent.com/57095736/165777394-7a685e38-fb82-4863-83c4-36fc4861deee.png)

- Configurar websocket OBS: primero nos dirigimos a la función startStreaming y copiamos la contraseña de la variable password, a continuación abrimos el programa OBS y pulsamos en herramientas -> Configuración del servidor WebSocket, ponemos las mismas opciones que en la foto inferior y pegamos la contraseña.

![image](https://user-images.githubusercontent.com/57095736/165780882-b79284b6-1ec7-40d3-804e-6309717ce68a.png)

### 5. Configurar torneo

- Crear un torneo: accedemos a Unibotics con el usuario instrumentar que tenga asignado el rol de "maestro", esto lo podemos ver en la tabla de usuario del repositorio de Unibotics Webserver. En la zona de crear un nuevo torneo elegimos la plantilla del ejercicio en la que se basará el torneo, fecha límite de inscripción (no pongas el mismo día en el que te encuentra o inferior) y día en el que se celebrará el torneo.

![image](https://user-images.githubusercontent.com/57095736/165782148-fd9aa996-8dc4-4a7d-b2ba-026f4519c6b8.png)
 
- Aprovechando que estamos con el maestro de ceremonias pulsamos en la opción de editar torneos y nos copiamos el id del torneo que hemos creado y el nombre del ejercio (lo necesitaremos más adelante).

![image](https://user-images.githubusercontent.com/57095736/165782755-130babfe-2650-4ad4-a30b-b63b7618bc3e.png)

- Volvemos a entrar a Unibotics con algún usuario que tenga rol de estudiante, y pulsamos en la opción de ver torneos y seleccionamos el torneo que hemos creado en el paso anterior, y pulsamos en el botón de apuntarse, si refrescamos apareceremos en la tabla de partcipantes. Podemos repetir este paso con los usuario que queramos.

- Nos vamos al archivo run.py de la carpeta raul (CAMBIAR ESTO) y en la variable tournamentID y tornamantExercise ponemos el id y ejercicio del torneo que copiamos en el paso anterior 

### 6. Diferencias D1 y D2

- D1: cuando estamos realizando un despliegue D1 signifíca que todo está en local en nuestra máquina, por lo tanto debemos arrancar el contenedor de MySQL, ElasticSearch, RADI y servidor (manage.py), si queremos desplegarlos y pararlos de manera automática ya depende de nuestra elección como vimos en el apartado 3.
- D2: cuando realizamos un despliegue D2 el código se divide en dos partes, el servidor se está ejecutando en el ordenador remoto del laboratio el cual nos está proporcioando de manera automática MySQL, ElasticSearch y servidor (manage.py), por lo tanto **nosotros no debemos lanzarlos**, solo debemos lanzar el RADI. Además debemos entender que el archivo run.py y torneoautomático.py se ejecutaráne en nuestro ordenador ya que los debemos lanzar para activar Selenium y la automátización del torneo, emisión de Twitch y maestro de ceremonias.

![image](https://user-images.githubusercontent.com/57095736/166100136-82cb59e2-05dd-4d43-b790-d9d22154e16c.png)


 




# Semana 11
- Se ha conseguido realizar un despligue D2 del proyecto, se han tenido que hacer tres cambios sobre el código: añadir excepciones en los accesos a ElasticSearch en caso de no existir la tabla, el código del websocket con OBS se ha pasado de la parte del servidor al cliente donde se ejecuta selenium y pur último el cliente ya no accede a ElasticSearch, esto daba problemas en D2 al ejecutarse el contenedor de ES en el ordenador remoto.

- Se han avanazado en la memoria del TFG y cambios en el índice del mismo

# Semana 10
- El objetivo de esta semana iba a ser intentar pasar el proyecto de D1 a D2 pero debido a que ha coincidido con Semana Santa no se nos han podido conceder los permisos necesarios para ello, entonces hemos comenzando con la memoria del TFG planteando el índice y resumiendo todo lo que se ha abordado en el mismo.

# Semana 9
- Se ha conseguido automatizar arreglar el problema con el cerebro del robot, se debía arrancar el RADI antes que el navegador. El torneo está autmatizado al 100%  incluyendo lanzamiento y cierre de los contenedores docker, server y directo con OBS.

- Se ha incluido los plug-in chosen.js y dataTable.js para mejorar el aspecto de tablas y formularios.

- Se han añadido códigos de prueba de los alumnos del Master en Visión Artificial para simular un torneo de prueba.

- Se ha preparado un pequeño a [video](https://www.youtube.com/watch?v=tITR2VZ2qig) a modo de resumen para el canal de JdeRobot

# Semana 8

- Automatizar el lanzamiento y cierre de los contenedores docker de Elastic Search, MySQL y RADI,programa OBS y lanzar el servidor. Este objetivo ha sido el más complejo y no se ha podido terminar, debido a que el navegador no es capaz de conectarse al cerebro del robot cuando el contenedor es lanzado por Selenium.

-  Añadir a la base de datos de los torneos las fechas de: límite de registro, día del evento y última modificación.

- Se ha creado una nuevo vista donde el maestro puede editar los torneos

- Traducir código al ingles.

# Semana 7
- Concentrar en la página del torneo toda la información (participantes, resultados, emisión en vivo, actualización en tiempo real y apuntarse a un torneo)

![image](https://user-images.githubusercontent.com/57095736/160450620-6dca1293-9b53-479f-9454-92e9ffd486c7.png)

- Ocultar el código fuente en la vista del maestro (está hecho pero desactivado durante el desarrollo por verificar el correcto funcionamiento del mismo)

![image](https://user-images.githubusercontent.com/57095736/160450953-c698b783-1616-4eac-b1f8-dbd7ad011e8f.png)

- Avanzar en la estructura de la base de datos en Elastic Search, se ha mejorado la estrucutra para soportar múltiples torneos, que un usuario se pueda apuntar a varios torneos, recoger el código dependiendo del torneo...

- Incrustar en el front-end una ventana con la emisión de twitch en directo

- Permitir a Selenium iniciar directo pulsando un botón. Este paso ha sido complejo, se ha usado un plug-in de web-sockets para obs el cual nos permite crear una conexión en el puerto 4444 para dar órdenes, permitiendo iniciar directo y más funciones.

![image](https://user-images.githubusercontent.com/57095736/160451762-3542c77a-67f1-47b7-a1e0-f1a007140e7e.png)
![image](https://user-images.githubusercontent.com/57095736/160451966-173e816e-9c44-4674-98a6-ec9727de3f04.png)

https://user-images.githubusercontent.com/57095736/160453447-dd85ecbc-6c97-4147-8c72-e5b00f350313.mp4


# Semana 6
Esta semana:
   - He aprendido a usar de manera básica elastic search, para poder escribir de manera rápida los resultados de los torenos. He creado el documento torneo, donde se       guarda id del torneo, nombre y puntuación.
   - Botón donde un usuario escribe su nombre y se apuntua a un torneo.
   - Selenium es capaz de iterar variar veces sobre los códigos de los usuarios y mandar al servidor los resultados, donde se escriben en Elastic Search.
   - En la página de resultados se muestran estos por orden, de mejor puntuación a peor.
   - En el video solo vemos los dos primeros usuarios, faltaría el tercero pero la memoria de grabación no daba para más.
  
  

https://user-images.githubusercontent.com/57095736/159039553-cc1596ee-ec1d-498f-8b3f-66a33ca51860.mp4

   - Finalmente si nos vamos a la página de puntuación vemos los resultados de la prueba.
   
![image](https://user-images.githubusercontent.com/57095736/159039894-79ba5846-aa6d-4b9f-9176-1ba2caf2f276.png)

# Semana 5 
Esta semana se han complentado varios objetivos esta semana:
  - Menú básico del maestro con todos los ejercicios disponibles
  - Plantilla dinámica para el maestro de ceremonia, en base al ejercicio pedido muestra una u otra utilizando herencia.
  - Permitir al maestro cargar código de un usuario en el editor de código del ejercicio. 
  - Automatizado con selenium todo el proceso desde registrarse hasta cargar el código del usuario.
Se soluciono un problema que complicó bastante  semana, en el código fuente de unibotics había una función que provocaba que al entrar a un ejercicio ya no podías navegar a ninguna otra página, lo encontré y comuniqué a Unibotics, me dieron permiso para eliminar la llamada.

![image](https://user-images.githubusercontent.com/57095736/159033254-569834db-b518-4951-9b39-9f3a4cea4fb1.png)

![image](https://user-images.githubusercontent.com/57095736/159033391-4d820fb5-a84a-4d48-b6c5-1169cbe61344.png)

# Semana 4
Ya hemos comenzado a trabajar en el tfg, ya añadí en la base de datos el nuevo rol que desarrollaremos, el Maestro de Ceremonias, el cual podrá pedir códigos de otros usuarios para evaluarlos y posteriormente mandarlos al servidor para crear una clasificación. De momento solo muestra una frase si es el usuario maestro de ceremonias. o no.

![image](https://user-images.githubusercontent.com/57095736/159032133-5d17fd97-b76e-4b47-8096-aa21e7d4429b.png)
![image](https://user-images.githubusercontent.com/57095736/159031674-80e935cc-4d66-4fcf-80c9-f90ec64e1eec.png)

Además estuve toda la semana con tutoriales de como funciona django, ya que es una tecnología que no había usado nunca y estaba provocando que me bloquease. Pero ya comprendo como funciona el sistema de modelo-vista-plantilla de cara a la siguiente semana. 

# Semana 3
Esta semana estuvo enfocado en aprender a utilizar un tecnología de automatización de tareas, Selenium. Estuve toda la semana aprendiendo a utilizarla,  termine creado un pequeño programa que se registra en Unibotics y lanza un ejercicio. Además de seguir viendo el código fuente.

https://user-images.githubusercontent.com/57095736/159031002-cca63b37-5512-4277-80af-cad74efbed6b.mp4

# Semana 2

Comencé instalando el web server en mi ordenador, me llevo unos días ya que tuve problemas con las instrucciones y la instalación en Windows. Ayudé a resolver algunos errores nuevos para completar las instrucciones.

Terminé de comprender la arquitectura que usan en Unibotics, es la siguiente:
1. Un repositorio donde almacenan todo el front end de la aplicación, es decir los eventos JS asociados a los botones, envió de mensajes... además de las diferentes platillas HTML de los ejercicios.
2. Un repositorio donde almacenan toda las base de datos Django, ahí se debe de almacenar la mayoría de la información persistente como perfiles de usuario...
3. Un último repositorio que actúa como back end, donde se ejecuta el cerebro del robot, simulación...

Posteriormente leí el TFM de Pablo Moreno, consistió en la implementación de WebRTC para poder crear juegos síncronos (la mayoría de su TFM se basó en la implementación de esta tecnología). Permitiéndole crear torneos y ejercicios tanto síncronos como asíncronos. 
También leí el TFG de Daniel Hervás sobre Gamificación en Unibotics, parece que se basó en pasar el trabajo de de Pablo Moreno de Kibotics (orientado a niños) a Unibotics (orientado a adultos), además de algunas añadiciones como teleoperar el robot.

Por último me informé sobre como implementar gamificación en educación ( 
[Gamificación en educación.pptx](https://github.com/RoboticsLabURJC/2022-tfg-raul-fernandez/files/8110740/Gamificacion.en.educacion.pptx) 
), serían los pasos que me gustaría seguir en Unibotics, pero necesitaré mucha más información sobre el público de esta plataforma, ver en que enfocamos el TFG...

# Semana 1
El 8 de febrero de 2022 tuvimos la primera reunión de TFG con mis tutores Daniel Palacios y Jose María Cañas Plaza.
Primero estuve instalando docker, y aprendiendo como funciona y sus componentes, donde destaco dockerfile, imagen y contenedor:
  - Dockerfiles: instrucciones en un txt sobre que de debe importar y como construir nuestra imagen.
  - Imagen: en nuestro ordenador almacenamos diferentes imágenes, que al hacerlas correr en un **contenedor** obtenemos el entorno que queremos simular

Posteriormente se me mandó familizarme con la página de Unibotics (versión online) y Robotics Academy (versión offline), realizando el ejercicio de follow the line. Donde aprendí un manejo muy básico de python y open CV.

Por último he estado revisando todo el código de su [github](https://github.com/JdeRobot/RoboticsAcademy), donde destaco los siguientes componentes:

1. Parecen hacer uso de 5 websockets, pero resalto 3 de ellos.

  2. **Websocket Manager** en el puerto 8765 (scripts/manager.py), hace uso de una clase *manager* para manejar todos los eventos del cliente/servidor, una clase *commands* que implementa la acción correspondiente a los eventos de la clase manager (arrancar el ejercicio seleccionado por el usuario, empezar/parar servidor gazabo/VNC, controlar la simulación es decir pararla, reanudarla... )  
 
  3. **Websocket code** (exercises/static/exercise/ejercicio que quieras/web-template/exercise.py), corresponde con el websocket puerto 1905. Sirve para interactuar con el cerebro del robot del ejercicio, que usando los comandos indicados en su github podemos mandarle nuestro código, resetear al robot... Además separa la parte de código secuencial e iterativo (eso luego luego se manda al manager.py donde se revisa si esta correcto el código). Además hace uso de la funciones GUI (relacionadas con la interfaz de ese ejercicio, velocidad del coche, ver lo que ve el robot...) y HAL (para acceder/mandar información a los actuadores del robot como velocidad angular, giro...)  
  4. **Websocket GUI** (exercises/static/exercise/ejercicio que quieras/webtemplate/gui.py) en el puerto 2303, manejo de la interfaz gráfica del ejercicio, dependiendo del ejercicio en el que nos encontremos tendremos una información u otra. 
  







