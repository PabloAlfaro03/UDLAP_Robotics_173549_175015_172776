# {Proyecto: Plannar Drawing Robot}  
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

The developed application, titled Planar Drawing Robot, is an interactive graphical interface built in MATLAB App Designer. It enables users to simulate the drawing behavior of a 3-degree-of-freedom (3-DOF) planar robot by processing an input image and generating corresponding joint trajectories. 

The user interface is designed for clarity and intuitive use, consisting of a central image panel, a set of control buttons, and a slider for image processing. The complete workflow is divided into five main stages: 

1. Image Acquisition 

Users may choose to either load an existing image from their local computer or capture a new image using the device's integrated camera. This process is facilitated through four buttons: 

Load Image: Opens a file browser for selecting an image file. The system supports .jpg format exclusively due to internal limitations in MATLAB’s imread() function. 

Turn On Camera: Activates the webcam and displays a live video feed in the Selected/Real-Time Image panel. 

Take Picture: Captures the current frame from the camera feed and displays it within the interface. 

Turn Off Camera: Closes the camera feed to prevent resource conflicts and ensure stable performance. 

A text field labeled Image Path is automatically populated when loading an image from disk, helping the user verify the selected file. 

2. Image Processing 

Once the image is loaded or captured, it must be processed to extract relevant contours that the robot will draw. This is done via: 

Process Level (Slider): Determines the threshold or sensitivity applied during edge detection. Lower values yield simplified contours with fewer points, while higher values retain more detail but increase trajectory complexity. 

Process (Button): Applies the selected processing level, updating the Processed Image panel to visually reflect the contour detection result. 

Different slider values generate significantly different contour maps, allowing for testing and optimization based on drawing complexity and execution time. (See Figures: “Processed Image – Low”, “Medium”, and “High”). 

3. Trajectory Generation 

The contours detected are decomposed into a series of ordered pixel coordinates known as waypoints. These waypoints are spatially grouped based on continuity and proximity to form coherent sub-trajectories. This reduces erratic motion and allows for smooth robotic movements. Each group is treated as a separate path segment, emulating a natural "stroke" in the drawing. 

The coordinates are scaled and translated into the robot’s operational workspace, forming the basis for inverse kinematics computation. 

4. Simulation Execution 

Once the user is satisfied with the processed image, they initiate the drawing by pressing: 

Robot Planar (Button): This command triggers a simulation window where the planar robot follows the computed trajectory. The robot is animated in real-time using the Peter Corke Robotics Toolbox. 

To enhance stability and readability of the simulation, delays are intentionally added between successive waypoints. This prevents jittering or undefined motion when encountering missing or extreme values (e.g., NaN entries in the data). 

5. Output Visualization 

The drawing sequence is visually replicated by the robot arm, showing how each path segment is traced in order. The final simulation visually matches the contour of the input image, demonstrating successful integration of image processing and robotic motion control. 

Program Structure and Code Explanation 

The application is implemented as an object-oriented program using MATLAB’s App Designer framework, which organizes the interface and logic into a class-based architecture. All components, such as buttons, sliders, image panels, and their associated behaviors, are encapsulated within a single app class that manages their properties and callbacks. 

1. Initialization and Component Setup 

Upon launching the app, the constructor method is automatically called to initialize the user interface. During this phase, all graphical components are rendered and positioned, including the layout for image panels, control buttons, text fields, and the process level slider. At this stage, default values for internal variables are also defined (e.g., empty image paths, blank waypoints, flags for camera state). 

2. Image Loading and Display 

When the user selects the Load Image button, a file dialog is triggered to allow the selection of a .jpg file from the local system. The selected image is loaded into memory using MATLAB’s standard image reading functions and is then displayed on the left side of the interface. If the user instead uses the camera, the app activates the webcam using MATLAB’s webcam support. A live preview feed is embedded in the UI, and a captured frame can be frozen and stored for processing. In both cases, the image is internally stored in a variable for further use. 

3. Image Processing and Waypoint Extraction 

The core of the system lies in its image processing pipeline. When the Process button is pressed, the image—either from disk or camera—is first converted to grayscale and filtered to enhance edges. Edge detection is then performed using a fixed algorithm (e.g., Canny or Sobel), with its sensitivity adjusted through the slider labeled Process Level. The resulting binary image is analyzed to extract contours, which are then sampled into discrete pixel coordinates. 

These coordinates, called waypoints, are stored in the workspace and used for trajectory generation. The code also includes logic to group waypoints into continuous paths, reducing disjointed movement and improving the realism of the drawing. 

4. Inverse Kinematics and Trajectory Planning 

Once the waypoints are defined, the inverse kinematics solver—provided by the Robotics Toolbox—is used to compute the joint angles required to reach each point. The robot model is configured based on predefined Denavit–Hartenberg (DH) parameters, corresponding to the structure of a planar 3R arm. For each waypoint, a set of joint angles is calculated and stored in sequence, forming the robot’s full drawing trajectory. 

Special care is taken to handle exceptions such as unreachable points or undefined solutions (e.g., NaN values), which are filtered or smoothed to maintain stable motion. 

5. Robot Simulation and Animation 

The final sequence is executed when the Robot Planar button is pressed. A new figure window is generated showing the simulated robot arm. Using animation loops, the robot iteratively updates its joint configuration according to the computed trajectory. A deliberate delay is introduced between frames to allow the user to visually follow the motion and to avoid instability in the rendering caused by rapid transitions. 

The animation is synchronized with the stored waypoints, ensuring that the robot's tool tip follows the intended path in a smooth and coherent manner. 

6. Resource Management and Cleanup 

The application also includes logic for managing system resources, particularly when working with the camera. Functions are provided to correctly release hardware handles, stop live previews, and close figures when not needed, avoiding common runtime issues in MATLAB. 

## ✅ Conclusión

The implementation of the Planar Drawing Robot successfully demonstrates the integration of image processing and robotic motion control within a single interactive platform. By converting visual input into waypoints and executing corresponding movements through inverse kinematics, the system achieves a functional simulation of automated drawing using a 3-DOF planar robot. The user interface proved intuitive and effective, allowing real-time interaction with both image acquisition and robot behavior. 

However, there are several potential improvements that could enhance both functionality and realism. Future iterations could include: 

Support for additional image formats such as .png or .bmp, increasing flexibility in input options. 

Contour simplification algorithms to dynamically reduce the number of waypoints while preserving shape fidelity, improving execution speed. 

Stroke-order optimization to minimize total travel distance, simulating a more natural drawing sequence. 

Integration with physical hardware, such as stepper motors or servo-driven robotic arms, to transition from simulation to real-world execution. 

Camera calibration and perspective correction to improve the accuracy of real-time image capture and preprocessing. 

These improvements would extend the educational and experimental value of the system, allowing for more advanced applications in robotics, automation, and computer vision. 

## 🔜 Mejoras futuras

- Enlistar las mejoras a realizar

## ⚠️ Advertencia

This application was developed strictly for academic and educational purposes within a controlled environment. It is intended as a simulation tool and should not be deployed in industrial or safety-critical contexts without proper validation, testing, and supervision. 

The authors assume no responsibility for any malfunction, hardware damage, or data loss that may occur as a result of improper use, external modification, or integration with unsupported devices. Users are advised to operate the application exclusively on supported MATLAB versions and to verify all image inputs and hardware compatibility beforehand. 

Any replication, distribution, or extension of this software must be done acknowledging its prototype status and under the same academic context for which it was created. 

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

