# {Proyecto: Nombre del Proyecto Simulado}  
![MIT License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)  
![Maintained](https://img.shields.io/badge/status-maintained-brightgreen?style=for-the-badge)  
![MATLAB](https://img.shields.io/badge/MATLAB-0076A8?style=for-the-badge&logo=mathworks&logoColor=white)  

Breve descripción del proyecto

This project presents the implementation of a planar 3-degree-of-freedom (3-DOF) robotic arm designed to perform automated drawing tasks on a flat surface. The system processes an input image to extract relevant waypoints, which are then used to generate joint trajectories through inverse kinematics. The drawing is simulated in a custom graphical interface developed in MATLAB.

## 📋 Requisitos Previos

The implementation of the project required the following technical and software components: 

MATLAB R2023a or higher, including the Image Processing Toolbox for contour extraction. 

Robotics Toolbox for MATLAB (Peter Corke), used for modeling and controlling the planar robotic arm. 

PC with minimum specifications: Intel i5 processor, 8 GB RAM, and Windows 10 or equivalent operating system. 

Graphics rendering capability to support animation and simulation of the robot’s motion. 

Basic familiarity with inverse kinematics and robotic arm modeling, as well as prior knowledge of MATLAB scripting. 

## 📖 Introducción

This project focuses on the simulation of a planar 3-degree-of-freedom (3-DOF) robotic arm designed to replicate the contours of an input image through automated drawing. The system employs image processing techniques to extract the external boundaries from a binary version of the input image. These contours are decomposed into sets of ordered coordinates, referred to as waypoints, which represent the trajectory that the robot must follow. To facilitate the execution of the drawing, waypoints are grouped based on their spatial continuity and proximity, allowing the robot to follow coherent paths with minimal unnecessary repositioning. Each group of waypoints corresponds to a distinct stroke or contour fragment, thus reducing the number of abrupt movements and enhancing the smoothness of the drawing. The inverse kinematics for each waypoint are computed using the Robotics Toolbox for MATLAB, enabling the real-time simulation of the robot’s motion. This project demonstrates the integration of image analysis, kinematic modeling, and trajectory planning within a simulated robotic environment, and lays the groundwork for future implementation on physical robotic platforms. 

## 🔧 Entorno de Simulación

The entire application was developed and executed within the MATLAB R2024a environment, using its App Designer for graphical interface construction. All simulations and robotic modeling tasks rely on the academic installation of: 

MATLAB R2024a 

Image Processing Toolbox 

Robotics Toolbox for MATLAB (version 10.4) 

This simulation environment allows for seamless integration of image analysis, numerical computation, and robotic visualization, ensuring compatibility and ease of use for educational purposes. The system was tested exclusively on Windows 10, though MATLAB ensures cross-platform support on Linux and macOS under equivalent configurations. 

## 💾 Instalación de Software

Pasos detallados para instalar y configurar el entorno de simulación:

- Instalación de simulador

- Instalación de ROS (si se usa)

- Dependencias y librerías necesarias

---

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

Código de ejemplo con explicación de cada parte relevante:

---

## ✅ Conclusión

Resumen de lo que se logró construir, aprendizajes obtenidos y posibles mejoras o versiones futuras del proyecto.

---

## 🔜 Mejoras futuras

- Enlistar las mejoras a realizar

## ⚠️ Advertencia

Como se indica en la licencia MIT, este software/hardware se proporciona **sin ningún tipo de garantía**. Por lo tanto, ningún colaborador es responsable de **cualquier daño a tus componentes, materiales, PC, etc..**.

---

## 📚 Recursos Adicionales

---

## 👥 Autores del proyecto

Autores originales del proyecto

---

## 📬 Contacto

¿Tienes dudas o sugerencias?

- 📧 Correo electrónico: ejemplo@udlap.mx

---

