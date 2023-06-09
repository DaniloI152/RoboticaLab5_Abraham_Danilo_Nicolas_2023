# Laboratorio 5 Robótica
## Integrantes: 
- Danilo Enrique Insuasty Delgado.
- Abraham Másmela Ramirez.
- Nicolás Prieto Solano.
## Descripción
Se busca desarrolar el modelo cinemático inverso del Phantom X e implementar rutinas de escritura que el usuario debe elegir.
## Objetivos:

• Determinar el modelo cinemático inverso del robot Phantom X.<br>
• Generar trayectorias de trabajo a partir del modelo cinemático inverso del robot.<br>
• Implementar el modelo cinemático inverso del robot en MATLAB o Python.<br>
• Operar el robot usando ROS a partir de trayectorias generadas en MATLAB o Python.<br>

## Desarrollo:
### Cinemática inversa
Se recuerda los parametros y las orientaciones DH del robot pincher
<div>
<p style = 'text-align:center;' align="center">
<img src="https://github.com/DaniloI152/RoboticaLab5_Abraham_Danilo_Nicolas_2023/blob/main/Imagenes/dh%20pincher.png" width="500px" >
</p>
</div>
Para facilitar el hallazgo de los diferentes angulos del robot pincher se analiza el vector de la muñeca y no el vector del tool. 
<div>
<p style = 'text-align:center;' align="center">
<img src="https://github.com/DaniloI152/RoboticaLab5_Abraham_Danilo_Nicolas_2023/blob/main/Imagenes/pw%20desplazado.png" width="500px" >
</p>
</div>
se reconocer que el vector de la muñeca es el mismo vector tool menos un desplazamiento L en la direccion de a.

<div>
<p style = 'text-align:center;' align="center">
<img src="https://github.com/DaniloI152/RoboticaLab5_Abraham_Danilo_Nicolas_2023/blob/main/Imagenes/formula%20pw.PNG" width="150px" >
</p>
</div>

Se analiza la vista superior del robot para hallar el angulo 1

<div>
<p style = 'text-align:center;' align="center">
<img src="https://github.com/DaniloI152/RoboticaLab5_Abraham_Danilo_Nicolas_2023/blob/main/Imagenes/vosta%20superior.PNG" width="400px" >
</p>
</div>

<div>
<p style = 'text-align:center;' align="center">
<img src="https://github.com/DaniloI152/RoboticaLab5_Abraham_Danilo_Nicolas_2023/blob/main/Imagenes/formula%20theta1.PNG" width="150px" >
</p>
</div>

Se analiza la vista lateral para hallar los angulos theta2 y theta3

<div>
<p style = 'text-align:center;' align="center">
<img src="https://github.com/DaniloI152/RoboticaLab5_Abraham_Danilo_Nicolas_2023/blob/main/Imagenes/vista%20lateral%201.PNG" width="400px" >
</p>
</div>

se halla un pw2 auxiliar para hallar estos angulos mas facilmente
<div>
<p style = 'text-align:center;' align="center">
<img src="https://github.com/DaniloI152/RoboticaLab5_Abraham_Danilo_Nicolas_2023/blob/main/Imagenes/formula%20pw2.PNG" width="150px" >
</p>
</div>
con este pw2 se halla primero el angulo theta3 con la ley del coseno

<div>
<p style = 'text-align:center;' align="center">
<img src="https://github.com/DaniloI152/RoboticaLab5_Abraham_Danilo_Nicolas_2023/blob/main/Imagenes/ley%20del%20coseno.PNG" width="250px" >
</p>
</div>

finalmente se obtiene theta3

<div>
<p style = 'text-align:center;' align="center">
<img src="https://github.com/DaniloI152/RoboticaLab5_Abraham_Danilo_Nicolas_2023/blob/main/Imagenes/theta3.PNG" width="250px" >
</p>
</div>

Se vuelve a analizar la vista lateral pero ahora en busca del theta2, para esto se deben hallar los angulos alpha y psi como se muestra en la imagen

<div>
<p style = 'text-align:center;' align="center">
<img src="https://github.com/DaniloI152/RoboticaLab5_Abraham_Danilo_Nicolas_2023/blob/main/Imagenes/vista%20lateral%2021.PNG" width="400px" >
</p>
</div>

<div>
<p style = 'text-align:center;' align="center">
<img src="https://github.com/DaniloI152/RoboticaLab5_Abraham_Danilo_Nicolas_2023/blob/main/Imagenes/desarrollo%20theta2.PNG" width="250px" >
</p>
</div>
finalmente se obtiene theta2

<div>
<p style = 'text-align:center;' align="center">
<img src="https://github.com/DaniloI152/RoboticaLab5_Abraham_Danilo_Nicolas_2023/blob/main/Imagenes/theta2.PNG" width="350px" >
</p>
</div>

el angulo thetha4 se obtiene de la siguiente forma
<div>
<p style = 'text-align:center;' align="center">
<img src="https://github.com/DaniloI152/RoboticaLab5_Abraham_Danilo_Nicolas_2023/blob/main/Imagenes/theta4.PNG" width="100px" >
</p>
</div>





















### Trayectorias
Para las trayectorias en primer lugar se realizó un dibujo del espacio de trabajo utilizando Dynamixel wizard, se tomaron medidas y luego se trazaron dos circulos con estas dimensiones en Autocad, para determinar donde iban a estar ubicados los puntos de las figuras a realizar. 
<div>
<p style = 'text-align:center;' align="center">
<img src="https://github.com/DaniloI152/RoboticaLab5_Abraham_Danilo_Nicolas_2023/blob/main/Imagenes/trayect.png" width="500px" >
</p>
</div>
Para la obtención de los puntos se colocó la ubicación de los puntos en autocad sobre las trayectorias de las figuras y se obtuvieron las coordenadas, que posteriormente se pasaron a python como una lista de vectores con tres coordenadas (x,y,z) y las coordenadas z se modificaron manualmente de tal forma que cuando estaba dibujando Z era cero y cuando habia un salto en la trayectoria se aumentaba Z para que el marcador no dibujara.
<div>
<p style = 'text-align:center;' align="center">
<img src="https://github.com/DaniloI152/RoboticaLab5_Abraham_Danilo_Nicolas_2023/blob/main/Imagenes/puntos.png" width="500px" >
</p>
</div>
Para las letras se tomaron los puntos, para el circulo se tomo una posición y a partir de ella con una función se trazo un circulo aumentando el angulo gradualmente, las figuras se pueden ver en la siguiente imagen

<div>
<p style = 'text-align:center;' align="center">
<img src="https://github.com/DaniloI152/RoboticaLab5_Abraham_Danilo_Nicolas_2023/blob/main/Imagenes/Trayectorias/todo.jpg" width="500px" >
</p>
</div>

<h2>Código</h2>
<img src="Imagenes/Code/Imports.png" width="500px" >
<p>Al iniciar el codigo se importan las librerias necesarias, siendo estas rospy para el manejo de ROS, numpy para operaciones numericas, rtb para la creacion del modelo matematico del robot y distintos topics de mensajes para la comunicacion con el manipulador pincher. Luego se crea el modelo de DHstd del robot pincher mediante la libreria std, definiendo las 4 articulaciones que posee el manipulador. De manera adicional se emplean las librearias de cv2 y pyplot para mostrar las imagenes que representan a la trayectoria del marcador.</p>
<img src="Imagenes/Code/c_inversa.png" width="500px" >
<p>En la cinematica inversa se definen las longitudes del robot junto unas variables auxiliares con valores que se usan repetidamente durante la funcion, los valores de las distintas articulaciones esta dado en terminos de arcotangentes empezando por el valor del angulo de la tercera articulacion, siguiendo el calculo de la segunda y de la primera, <span>acabando finalmente con la cuarta articulacion siendo esta la que no fue resuelta de manera geometrica.</span> Estos valores son devueltos como una lista.</p>
<img src="Imagenes/Code/e_pos.png" width="500px" >
<p>Se crea la funcion encargada de enviar distintas posiciones al controlador del manipulador, se crea el objeto publisher que pasara los mensajes al pincher y se inicia el nodo de ROS que comunica al codigo de python, en un ciclo for que itera en la lista de puntos que se ingresan como parametros iniciales, se separa cada punto en sus coordenadas X, Y y Z. Se crea el objeto state que sera el mensaje publicado y el objeto point que correspondera a uno de los puntos de ntro de la JointTrajectory, en la variable posActual se guardan los valores de las artiuclaiones que son obtenidas mediante la funcion de cinematica inversa ya descrita, la posicion actual se añade a la variable de point y esta misma se anexa a la variable state que es publicada mediante el publisher ya creado, finalmente se suspende el programa brevemente para dar tiempo al pinche a ejecutar la instruccion.</p>
<img src="Imagenes/Code/e_ang.png" width="500px" >
<p>Similar a la funcion anterior se crea el elemento de publisher con el topi c de JointTrajectory, junto con el mensaje state de topic JointTrajectory, se inicializa el nodo de ROS y crea el objeto point de la clase JointTrayectoryPoint, a este ultimo se anexan los angulos que se reciben como parametros de entrada a la funcion, y este mismo se anexa al objeto state que es posteriormente publicado mediante el publisher, dejando un tiempo para la ejecucion de los comandos.</p>
<img src="Imagenes/Code/joint1.png" width="500px" >
<p>Se establece un posicion de home para el robot, sen envia a esta y luego mediante la funcion enviarPosicion se lleva al punto donde esta el marcador, este se recoje y luego se levanta para volver a la posicion de home. Se inicia un ciclo while que se mantendra activo siempre que el programa siga en ejecucion, pedira una entrada al usuario para definir la funcion a ejecutar, estas opciones son impresas mediante consola.</p>
<img src="Imagenes/Code/tarea1.png" width="500px" >
<p>Para el desarrollo de distintas tareas se sigue un procedimiento similar, primero se muestra una imagen que le ilustrara al usuario la trayectoria teorica que usara el robot. luego dentro de una lista de puntos se guarda el recorrido que debe de tener el marcador, con cada uno de estos puntos definido en sus coordenadas X, Y y Z, mandando la lista de los elementos de la trayectoria a la funcion enviarPosicion que se encarga del recorrido, cuando acabe este recorrido, el robot vuelve a la posicion de home mostrando por consola el tiempo de ejecuacion total.
  
### Resultados
A continuación se muestra el video del funcionamiento del robot realizando los dibujos seleccionados por el usuario:
<p align="center">
  <a href="https://youtu.be/J3g1518Dm50" target="_blank" rel="noreferrer">
    <img width="500px" src="https://github.com/DaniloI152/RoboticaLab5_Abraham_Danilo_Nicolas_2023/blob/main/Imagenes/videoicon.png"/>
  </a>
</p>
  
### Análisis de errores  
<p>Respecto a los errores entre las dimensiones teoricas y reales de los dibujos realizados por el robot se realiza esto a partir de paint.</p>
<img src="Imagenes/Resultados/Resultado1.png" width="500px" >
<p>Con la longitud aproximada de la tabla alrededor de 50 cm se puede hacer un simil entre la longitud de la tabla en pixeles, siendo esta cercana a los 273750 pixels, por lo que cada 10 pixeles de la figura representaran 1.826 mm de longitud real. Con esta relacion y las herramientas de medicion de pixeles que ofrece paint que dan la longitud en la horizontal y la vertical en pixeles, es posible mediante el teorema de pitagoras medir los pixeles de los distintos dibujos hechos por el robot y mediante la relacion de longitudes se puede obtener el valor en milimetros.</p>
<img src="Imagenes/Resultados/Dimensiones.png" width="500px" >
<p>Finalmente mediante las longitudes teoricas con las que se planteo el ejercicio se obtiene el error relativo para cada una de las medidas.</p>
<img src="Imagenes/Resultados/Errores.png" width="500px" >
De esto se puede ver que para las letras que poseen geometrias mas complejas que el circulo y las lineas de la x el porcentaje de error entre las dimensiones teoricas y las reales es mas alto, sin embargo algo que se ve al comparar el resultado teorico comparado con la imagen del resultado real es que las geometrias curvas como la del circulo no son perfectas, quedando un lado con una longitud mayor a la otra, 
<h2>Conclusiones</h2>

• La cinemática inversa permite lograr trayectorias complejas en el robot Pincher mediante ecuaciones simples, de tal forma que podemos  diseñar movimientos precisos y controlados de manera eficiente, aunque se debe tener en cuenta que la estructura del Pincher no suprime algunas vibraciones provocadas por los movimientos.

