# Inertia Wheel Pendulum
## MECA 482-02 Group 5: *Victor Alvarez, Xavier Andrade, Sean Murray, Samuel Kelly, John Voter*

## Introduction
**1. Background**

The inertia wheel pendulum is a system that seeks to stabilize a pendulum in the inverted upright position. This is to be acheived by calculated accelleration of an inertia wheel at the end of the pendulum arm. In order to achieve the desired functionality, one end of the pendulum arm is attached to a rotating base that is fixed to a table-end. An encoder serves as the rotating base in order to track the pendulum arm's angle of rotation. Figure 1 below captures the operational viewpoint for the system described above.

<p align="center">
<img width="550" alt="operationalViewpoint" src="https://user-images.githubusercontent.com/90480302/146479783-8992f72c-04e3-4042-ac6e-c24deac53aea.PNG">
</p>

<p align="center">  
  Figure 1: Operational viewpoint for the inertia wheel pendulum.
</p>

The given operational viepoint serves to give the reader a very top-level vizualization of the physical system. However, it is unclear as to how this system will acheive the desired functionality. In response, a logical/functional viewpoint was created to serve as a reference for how components within the system interact with onanother. Seen below in Figure 2 is the logical/functional viepoint for the inertia wheel pendulum.

<p align="center">
  <img width="600" alt="logicalViewpoint" src="https://user-images.githubusercontent.com/90480302/146479834-3edfd602-7af7-4eee-b9b2-dcb6e1c0be35.PNG">
</p>

<p align="center">  
  Figure 2: Logical/functional viewpoint for the inertia wheel pendulum.
</p>

When couple with Figure 1, the logical/functional viewpoint serves to provide a complete top-level unserstanding of system functionality.

The following report consists of documentation pertaining to the solution obtained by the team. In order to acheive the desired functionality a mathematic model wast obtained for the system, from there a controller architechture was devised to simulate and implement the derived mathematical model. The following report consists of documentation of the control system design process. 

**2. Resources**

Listed below are several key resources utilized by the team throughout the control system desing process (for full citation please see "References"):
   - *Control System Engineering*: 7th Edition; Norman S. Nice
   - *Engineering Science and Technology, an International Journal*: Nonlinear analysis and control of a reaction wheel pendulum: Lyapunov-based approach; Oscar Montoya & Walter Gonzales
   - *Object Heirarchy Relations - CopelliaSim*: Leopoldo Arnesto



## Modeling
**1. Free Body Diagram**

In order to derive the mathematical model for the inertia wheel pendulum, a FBD must first be constructed to define reference axes and system variables. Figure 3 below depicts the free body diagram used to define stem variables. 

<p align="center">
  <img width="354" alt="FBD" src="https://user-images.githubusercontent.com/90480302/146482480-46cb4d4e-19c1-4d3a-a63b-4c0769653998.PNG"> 
</p>

<p align="center">  
  Figure 3: FBD used to define analysis of the inertia wheel pendulum
</p>

The following table depicts definitions of the symbols present in the free body diagram seen above.
## Sensor Calibration
## Controller Design Simulation
## Controller Implementation
## Appendix A: Simulation Code
## References


