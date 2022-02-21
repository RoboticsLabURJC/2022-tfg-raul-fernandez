# 2022-tfg-raul-fernandez
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

