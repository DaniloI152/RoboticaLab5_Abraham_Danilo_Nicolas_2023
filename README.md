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
Para las letras se tomaron los puntos, para el circulo se tomo una posición y a partir de ella con una función se trazo un circulo aumentando el angulo gradualmente para la

<h2>Código</h2>
<img src="Imagenes/Code/Imports.png" width="500px" >
Al iniciar el codigo se importan las librerias necesarias, siendo estas rospy para el manejo de ROS, numpy para operaciones numericas, rtb para la creacion del modelo matematico del robot y distintos topics de mensajes para la comunicacion con el manipulador pincher. Luego se crea el modelo de DHstd del robot pincher mediante la libreria std, definiendo las 4 articulaciones que posee el manipulador.
## Conclusiones
