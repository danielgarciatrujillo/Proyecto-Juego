# Proyecto-Juego
## Resumen del juego
Este juego consiste en meter al usuario dentro de un escenario cuadrado de donde no puede salir ya que estará delimitado por muros y también con obstáculos que bloquean la vista y el movimiento libre por el escenario. Desde que empieza a correr el juego también se inicia un temporizador visible en el centro de la pantalla que inicia en 80 segundos, el juego se termina si el jugador logra conseguir 5 botiquines repartidos por todo el mapa en el tiempo establecido o en caso contrario se mostrará un mensaje diciendo que el tiempo se acabó y procederá a cerrarse automáticamente
## Requisitos para correr el juego
- Visual Studio (2015 o 2017)
- Tarjeta gráfica compatible con la librería OpenGL
- Librería glut opengl
## Funcionamiento del juego
### Primeros pasos
- Cuando el juego empieza, un temporizador que inicia en 8000 milisegundos u 80 segundos se muestra en pantalla y empieza a descender
- El jugador se puede mover libremente dentro del mapa delimitado por muros y obstáculos utilizando las teclas W para moverse hacia adelante, A para girar hacia la izquierda y D para girar a la derecha
- Es posible mantener presionado la tecla W para avanzar consecutivamente varios pasos hasta topar con un obstáculo
- Existen 5 botiquines repartidos por el mapa, el objetivo del jugador es recogerlos todos
- Para recoger un botiquín solo necesitas acercarte a la ubicación del mismo e intentar atravesarlo, el botiquín se quitara del mapa
- Cuando un botiquín es recogido, un mensaje junto al temporizador saldrá para decirle al jugador "una menos, corre!" y aumentando un contador interno que almacena la cantidad de botiquines que el jugador va recogiendo
### Condiciones de terminación
1.- El jugador consigue todos los botiquines, la ventana del juego se cierra y el programa termina
2.- El temporizador llega a 0, el siguiente mensaje es desplegado: "--> SE TE ACABÓ EL TIEMPO". El programa termina y la ventana de ejecución se cierra
### Lógica con la que se valida el funcionamiento de los botiquines y el temporizador
El temporizador es un valor de tipo entero que inicia con el valor 8000 que corresponde a los milisegundos que dura la ejecución del juego, para poder mostrarlos en pantalla usamos un arreglo de caracteres, para ello hacemos dos casteos, convertimos el 8000 en un valor de tipo string guardandolo en una variable del mismo tipo, después casteamos ese string para convertirlo en un arreglo de caracteres y los mostramos en pantalla con la función drawString(). El temporizador constantemente es evaluado y comparado con una variable de valor 0 llamada "timeout" para así saber cuando se acabó el tiempo y se cierre la ventana de ejecución con la función "exit(EXIT_SUCCESS)".
La recogida de botiquines se evalua en el metodo donde se evaluan las teclas presionadas, cuando una variable que sirve como bandera adquiere el valor de 1 significa que estamos justo en la posicion de un botiquin, asi que en ese mismo punto llamamos a la matriz que guarda las posiciones en el mapa y le damos el valor de 0 a esa misma posicicion, causando que el botiquin desaparezca. Despues de recoger la caja, se aumenta el valor de un contador interno de nombre "cajas" y se evalua con otra variable de nombre "maximas", cajas debe alcanzar el valor de maximas para poder terminar la ejecucion del programa en ese instante, en caso contrario, el juego sigue corriendo.
