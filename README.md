# 2022-tfg-raul-fernandez
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
  







