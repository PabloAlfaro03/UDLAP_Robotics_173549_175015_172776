# {Proyecto: Plannar Drawing Robot}  
![MIT License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)  
![Maintained](https://img.shields.io/badge/status-maintained-brightgreen?style=for-the-badge)  
![MATLAB](https://img.shields.io/badge/MATLAB-0076A8?style=for-the-badge&logo=mathworks&logoColor=white)  

Breve descripción del proyecto

El siguiente proyecto presenta la implementación de un brazo robótico planar de 3 grados de libertad (3-DOF) diseñado para realizar tareas de dibujo automatizado sobre una superficie plana de 2 x 2 x 1. El sistema procesa una imagen de entrada en formato JPG, para extraer puntos de referencia (waypoints) de las imágenes, que luego se utilizan para generar trayectorias articulares mediante cinemática inversa. El dibujo se simula en una interfaz gráfica personalizada desarrollada en una App de MATLAB.

## 📋 Requisitos Previos

La implementación del proyecto requirió los siguientes componentes técnicos y de software:

MATLAB R2023a o superior.

El add On, Image Processing Toolbox para la extracción de contornos. 

El add On, Robotics Toolbox for MATLAB (Peter Corke), utilizada para modelar y controlar el brazo robótico planar.

Una laptop o PC con las siguientes especificaciones: Procesador Intel i5, 8 GB de RAM, 512GB de almacenamiento y sistema operativo Windows 10, equivalente o superior 

Capacidad de renderizado gráfico para soportar la animación y simulación del movimiento del robot.

Conocimientos básicos de cinemática inversa y modelado de brazos robóticos, así como familiaridad previa de programación en MATLAB.

## 📖 Introducción

Este proyecto se centra en la simulación de un brazo robótico planar de 3 grados de libertad (3-DOF) diseñado para replicar los contornos de una imagen de entrada mediante dibujo automatizado. El sistema emplea técnicas de procesamiento de imágenes para extraer los bordes externos de una versión binaria de la imagen. Estos contornos se descomponen en conjuntos de coordenadas ordenadas llamadas waypoints, que representan la trayectoria que debe seguir el robot.
Para facilitar la ejecución del dibujo, los waypoints se agrupan según su continuidad espacial y proximidad, lo que permite al robot seguir trayectorias coherentes con reposicionamientos mínimos. Cada grupo de waypoints corresponde a un trazo o fragmento de contorno distinto, reduciendo movimientos abruptos y mejorando la suavidad del dibujo.
La cinemática inversa para cada punto se calcula usando el Robotics Toolbox para MATLAB, lo que permite una simulación en tiempo real del movimiento del robot. Este proyecto demuestra la integración del análisis de imágenes, modelado cinemático y planificación de trayectorias en un entorno robótico simulado, sentando las bases para una futura implementación en plataformas robóticas físicas.


## 🔧 Entorno de Simulación

La aplicación fue completamente desarrollada y ejecutada en el entorno MATLAB R2024a, utilizando el apartado de App Designer para la construcción de la interfaz gráfica. Todas las simulaciones y tareas de modelado robótico se basan en la instalación académica de:
•	MATLAB R2024a
•	Image Processing Toolbox
•	Robotics Toolbox para MATLAB (versión 10.4)
Este entorno de simulación permite una integración fluida del análisis de imágenes, cálculos numéricos y simulación robótica, asegurando compatibilidad y facilidad de uso con fines educativos. El sistema fue probado exclusivamente en Windows 10, aunque MATLAB garantiza compatibilidad multiplataforma en Linux y macOS con configuraciones equivalentes.

## 💾 Instalación de Software

Para la instalación de el software de MATLAB se deben hacer una serie de pasos:
1.	Utilizando el buscador de Google Chrome o Microsoft Edge, colocar en la barra buscadora Matlab, una vez obtenido el resultado entrar a la página oficial de MathWorks.

2.	Dar clic en el botón Get Matlab, una vez dado clic se abrirá una ventana nueva.

3.	En la ventana nueva crear una nueva cuenta o en caso de ya tener una vigente iniciar sesión.

4.	En el caso de crear una nueva cuenta, introducir un correo electrónico de empresa o universidad que cuente con la licencia de Matlab e introducir una contraseña de 8 caracteres.

5.	Una vez creada la cuenta se deberá introducir un código que llegará al correo proporcionado. Una vez introducido el código se activará la cuenta de Matlab y se deberá introducir más información como nombre, universidad o empresa, país, etc.

6.	Al concretarse la creación y activación de la cuenta, la pagina trasladara al usuario a Matlab Online donde se debe dar clic a la opción de instalar Matlab en la computadora.

7.	Dando click en instalar se abrirá una nueva ventana donde se debe escoger la versión de Matlab que se va a descargar (R2024a o superior).

8.	Una vez descargada la versión seleccionada, ir a la carpeta de descargas en la aplicación de archivos, dar clic derecho y ejecutar.

9.	 Después de descargar, se abrirá una ventana emergente donde se debe colocar nuevamente el correo y la contraseña de la cuenta previamente creada, iniciar sesión y aceptar el contrato de uso.

10.	Al iniciarse sesión por primera vez, se debe seleccionar una carpeta destino para los archivos de Matlab y posteriormente escoger el número de productos que ofrece Matlab, en este apartado escoger los productos necesarios para que la aplicación funcione. En este caso seleccionar Image Processing Toolbox y Robotics Toolbox para MATLAB (versión 10.4) junto con App Matlab.

11.	Dar clic en el botón siguiente e instalar.

12.	Finalmente, una vez realizada la instalación iniciar sesión por última vez con el correo y contraseña seleccionadas al inicio e utilizar Matlab.

Nota: En caso de no haber instalado los productos necesarios para utilizar la Aplicación ir al apartado de Home en la aplicación y seleccionar Add-Ons, y buscar las los productos necesarios para observar el funcionamiento de la aplicación.


## 🛠️ Configuración del Proyecto

Instrucciones para clonar el repositorio, compilar, lanzar el mundo simulado y ejecutar los nodos o scripts:

```bash
git clone https://github.com/usuario/proyecto-simulacion.git
cd proyecto-simulacion
catkin_make
source devel/setup.bash
roslaunch proyecto_simulacion main.launch
```

## 💻 Programación

La aplicación desarrollada, titulada Planar Drawing Robot, es una interfaz gráfica interactiva construida en el apartado de App Designer en MATLAB. Permite a los usuarios simular el movimiento de un robot planar de 3-DOF procesando una imagen de entrada y generando las trayectorias articulares correspondientes, creando un dibujo de la imagen procesada.
La interfaz de usuario está diseñada para ser clara e intuitiva, con un panel central de imagen, un conjunto de botones de control y un deslizador para ajustar el procesamiento de la imagen. El flujo de trabajo se divide en cinco etapas principales:

1. Adquisición de imagen

El usuario puede cargar una imagen desde su equipo (siempre que sea en formato JPG) o capturar una nueva con la cámara integrada. Este proceso se gestiona mediante cuatro botones:

•	Cargar Imagen: Abre el explorador de archivos para seleccionar una imagen en formato .jpg.

•	Encender Cámara: Activa la webcam y muestra el video en tiempo real.

•	Tomar Foto: Captura el cuadro actual de la cámara y lo muestra en la interfaz.

•	Apagar Cámara: Cierra el feed de la cámara para liberar recursos.
Un campo de texto llamado Ruta de Imagen se llena automáticamente al cargar una imagen, permitiendo verificar el archivo seleccionado.

2. Procesamiento de imagen

Una vez cargada o capturada la imagen, se procesa para extraer los contornos relevantes que el robot dibujará:

•	Nivel de Procesamiento (Deslizador): Controla la sensibilidad del algoritmo de detección de bordes. Valores bajos simplifican los contornos; valores altos retienen más detalles.

•	Procesar (Botón): Aplica el procesamiento y actualiza el panel de imagen procesada.

Distintos niveles del deslizador generan mapas de contornos significativamente diferentes, lo que permite ajustar según la complejidad del dibujo y el tiempo de ejecución.

3. Generación de trayectoria

Los contornos detectados se convierten en coordenadas ordenadas (waypoints), agrupadas según su continuidad espacial. Esto minimiza el movimiento errático y permite trazos más naturales.
Las coordenadas se escalan y transforman al espacio de trabajo del robot, siendo la base para el cálculo de la cinemática inversa.

4. Ejecución de simulación

Cuando la imagen procesada está lista, el usuario inicia el dibujo presionando:

•	Robot Planar (Botón): Abre una ventana de simulación donde el robot sigue la trayectoria calculada, animado en tiempo real con Robotics Toolbox.

Se añaden retardos intencionales entre puntos para mejorar la estabilidad visual y evitar errores de renderizado por transiciones rápidas o datos inválidos (por ejemplo, valores NaN).

5. Visualización de salida

El brazo robótico reproduce visualmente la secuencia de dibujo, siguiendo cada trazo en orden. La simulación final refleja el contorno de la imagen de entrada, demostrando la integración efectiva de procesamiento de imágenes y control de movimiento robótico.

Estructura del programa y explicación del código
La aplicación está implementada de forma orientada a objetos usando App Designer de MATLAB, organizando la lógica en una clase que gestiona todos los componentes (botones, sliders, paneles de imagen) y sus callbacks.

1.	Inicialización

Se ejecuta automáticamente al lanzar la app, configurando los componentes gráficos y las variables internas por defecto.

2.	Carga de la imagen

Se activa un diálogo para seleccionar un archivo .jpg o usar la cámara para capturar una imagen. Esta se guarda en memoria para su procesamiento.

3.	Procesamiento y extracción de waypoints

La imagen se convierte a escala de grises, se detectan bordes con un algoritmo (Canny o Sobel) y se extraen los contornos como coordenadas.

4.	 Cinemática inversa y planificación

Se define un modelo cinemático basado en parámetros DH. Para cada waypoint, se calculan los ángulos articulares. Se filtran puntos no alcanzables o inconsistentes.

5.	 Simulación y animación

Se genera una ventana con el robot animado siguiendo la trayectoria con retrasos entre cuadros para mejorar la visualización.

6.	Gestión de recursos

Se libera la cámara y se cierran ventanas cuando no se usan para evitar errores comunes de ejecución.
 
## ✅ Conclusión

La implementación del Planar Drawing Robot demuestra con éxito la integración del procesamiento de imágenes y el control de movimiento robótico en una única plataforma interactiva. Al convertir una imagen en una secuencia de movimientos mediante cinemática inversa, se logra una simulación funcional de dibujo automatizado. Sin embargo, a lo largo de la creación de la aplicación se observaron algunos detalles como la limitación de resolución de pantalla, ya que para monitores de 1920 x 1080 el diseño implementado se ve afectado y se observan palabras o colores encimados. De igual manera, el software de MATLAB genera algunas limitaciones en cuanto los formatos de imagen que se pueden procesar, ya que únicamente las imágenes JPG pueden ser procesadas, de igual manera la gama de colores que se puede procesar es RGB por lo que colores chillantes o neón no se pueden procesar. Aun que el nivel de detalle que se observa en las imágenes y la fluides de los movimientos del robot demuestran que la aplicación funciona de manera óptima para los objetivos fijados.

## 🔜 Mejoras futuras

•	Soporte para formatos de imagen adicionales como .png o .bmp.

•	Algoritmos de simplificación de contornos para reducir puntos sin perder fidelidad.

•	Optimización del orden de trazos para minimizar desplazamientos innecesarios.

•	Integración con hardware físico como motores paso a paso o servos.

•	Calibración de cámara y corrección de perspectiva para mejorar la captura en tiempo real.

Estas mejoras ampliarían el valor educativo y experimental del sistema para aplicaciones más avanzadas en robótica, automatización y visión por computadora.

## ⚠️ Advertencia

Esta aplicación fue desarrollada exclusivamente con fines académicos y educativos en un entorno controlado. No debe usarse en contextos industriales o críticos sin validación y supervisión adecuadas.

Los autores no se responsabilizan por daños, malfuncionamientos o pérdida de datos derivados del uso incorrecto, modificaciones externas o integración con dispositivos no compatibles. Se recomienda utilizar solo versiones compatibles de MATLAB y verificar la entrada de imágenes y el hardware antes de su ejecución.Cualquier reproducción o distribución del software debe reconocer su carácter de prototipo y mantenerse en el contexto académico original.

## 📚 Recursos Adicionales

Pagina oficial de Matlab: https://www.mathworks.com/products/matlab.html

Pagina oficial de Peter Corke: https://petercorke.com

Video del funcionamiento de la aplicación: https://youtu.be/bnFwH0hqel0

## 👥 Autores del proyecto
Equipo 6 de Robótica Indutrial:

Juan Pablo Alfaro Gaona id:173549

Santiago Suárez Martínez id:175015

Alan Baladier Nicolás Beltrán Durán id:172776

## 📬 Contacto

¿Tienes dudas o sugerencias?

Asesor encargado de la página: César Martínez Torres

- 📧 Correo electrónico:cesar.martinez@udlap.mx
