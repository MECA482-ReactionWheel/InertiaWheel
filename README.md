# Inertia Wheel Pendulum
## MECA 482-02 Group 5: *Victor Alvarez, Xavier Andrade, Sean Murray, Samuel Kelly, John Voter*

## Introduction
**1. Background**

The inertia wheel pendulum is a system that seeks to stabilize a pendulum in the inverted upright position. This is to be acheived by calculated accelleration of an inertia wheel at the end of the pendulum arm. In order to achieve the desired functionality, one end of the pendulum arm is attached to a rotating base that is fixed to a table-end. Incorporated into the system are two encoders, one serves as the rotating base in order to track the pendulum arm's angle of rotation while the other monitors wheel speed/position. Figure 1 below captures the operational viewpoint for the system described above.

<p align="center">
<img width="550" alt="operationalViewpoint" src="https://user-images.githubusercontent.com/90480302/146479783-8992f72c-04e3-4042-ac6e-c24deac53aea.PNG">
</p>

<p align="center">  
  <b>Figure 1</b>: Operational viewpoint for the inertia wheel pendulum.
</p>

The given operational viepoint serves to give the reader a very top-level vizualization of the physical system. However, it is unclear as to how this system will acheive the desired functionality. In response, a logical/functional viewpoint was created to serve as a reference for how components within the system interact with onanother. Seen below in Figure 2 is the logical/functional viepoint for the inertia wheel pendulum.

<p align="center">
  <img width="600" alt="logicalViewpoint" src="https://user-images.githubusercontent.com/90480302/146479834-3edfd602-7af7-4eee-b9b2-dcb6e1c0be35.PNG">
</p>

<p align="center">  
  <b>Figure 2</b>: Logical/functional viewpoint for the inertia wheel pendulum.
</p>

When couple with Figure 1, the logical/functional viewpoint serves to provide a complete top-level unserstanding of system functionality.

The following report consists of documentation pertaining to the solution obtained by the team. In order to acheive the desired functionality a mathematic model wast obtained for the system, from there a controller architechture was devised to simulate and implement the derived mathematical model. The following report consists of documentation of the control system design process. 

**2. Resources**

Listed below are several key resources utilized by the team throughout the control system desing process (for full citation please see "References"):
   - *Control System Engineering*: 7th Edition; Norman S. Nice
   - *Automatic Control with Experiments*: Victor Manuel Hernández-Guzmán & Ramón Silva-Ortigoza
   - *Nonlinear analysis and control of a reaction wheel pendulum - Lyapunov-based approach*: Oscar Montoya & Walter Gonzales
   - *Object Heirarchy Relations - CopelliaSim*: Leopoldo Arnesto
   - CopelliaSim Forum: *Shared Memory Plugin For VREP /Matlab Communication*

## Modeling
**1. Schematic**

In order to derive the mathematical model for the inertia wheel pendulum, a schematic must first be constructed to define reference axes and system variables. Figure 3 below depicts the system schematic used to define relevant variables. 

<p align="center">
  <img width="500" alt="FBD" src="https://user-images.githubusercontent.com/90480302/146482480-46cb4d4e-19c1-4d3a-a63b-4c0769653998.PNG"> 
</p>

<p align="center">  
  <b>Figure 3</b>: Symbolic schematic of the inertia wheel pendulum.
</p>

The following table depicts definitions based on the above schematic for system parameters used in the derivation of the mathematical model. 

<p align="center">
  <b>Table 1</b>: Parameter definitions relevant to preparing the mathematical model for the inertia wheel pendulum.
</p>

<p align="center">
  <img width="500" alt="parameterValues" src="https://user-images.githubusercontent.com/90480302/146488151-d394b5c8-8b78-4336-be7a-3dc923fa0ba7.PNG">
</p>

**2. Equation of Motion**

For mechanical systems, a classical method to derive the equations of motion is the Euler-Lagrange approach. As is well known, this approach requires the computation of kinetic and potential energies and the subsequent knowledge of the forces acting on the system. The equations shown below represent the Euler-Lagrange equation with both interacting bodies.

<p align="center">
  <img width="600" alt="eulerLagrange" src="https://user-images.githubusercontent.com/90480302/146493561-10e9f0d4-612e-42b9-aa01-c809d1890a51.PNG">
</p>

In Eq.(1), the zero on the right hand side indicates that no external torque is being applied to the pendulum at this point. The zero on the on Eq.(1) , indicates that no external torque is applied at the point where the pendulum hangs up since no potential force is being applied to the pendulum.

From here, the next step is to define the Lagrangian term depicted in the two equations above. The three equations below are general equations for: Lagrange, kinetic, and potential energies of a system.

<p align="center">
  <img width="600" alt="kineticPotential" src="https://user-images.githubusercontent.com/90480302/146494552-59c75951-86fb-45f1-89b7-4e05d3d46140.PNG">
</p>

The pendulum arm is a body with a mass distributed along its length. Its total kinetic energy is the summation of the kinetic energy of a particle of mass <i>m</i><sub>1</sub> translating a circumference of radius <i>l</i><sub>c</sub>, along with the kinetic energy of a bar that rotates around its center of mass. Kinetic energy can be taken into account that the wheel’s angular velocity, as measured by an observer fixed to the table, is <i>θ</i><sub>1</sub>+<i>θ</i><sub>2</sub>. The equations below define the system's total kinetic energy. 

<p align="center">
  <img width="600" alt="kineticEnergy" src="https://user-images.githubusercontent.com/90480302/146495700-238bc7b4-f702-4cc7-8740-fa5d7b16501e.PNG">
</p>

The final step in obtaining the system's Lagrangian equation is to define its potential energies. It has been assumed that when the angular position is 0 degrees (normal equlibrium state) the system's potential energy is 0 as well. The equations below define the potential energies within the system. 

<p align="center">
  <img width="600" alt="potentialEnergy" src="https://user-images.githubusercontent.com/90480302/146496570-8c30608a-f26e-4e05-a5a3-815b5d034045.PNG">
</p>

Finally, combining Eqs.(6, 7, 8, 9) into Eq.(4) yields the final Lagrange equation for the system shown in Eq.(10) below.

<p align="center">
  <img width="600" alt="lagrange" src="https://user-images.githubusercontent.com/90480302/146497214-0d58b9a8-3a4b-48f3-8085-92b82770f95f.PNG">
</p>

**3. State Space Representation**

With the equation of motion derived for the system, the final step in acquiring the mathematical model is to represent the system in state space. Seen below are the general equations for state space representation. 

<p align="center">
  <img width="600" alt="stateGen" src="https://user-images.githubusercontent.com/90480302/146600660-08907465-6ca7-43f5-b743-7b32ef30c958.PNG">
</p>

To represent the system in state space the phase variables must first be defined. Eq.(13, 14) below show the system-particular state variable definitions. 

<p align="center">
  <img width="600" alt="stateVars" src="https://user-images.githubusercontent.com/90480302/146602241-f28d12bd-717a-456b-af88-7e6216e04a3e.PNG">
</p>

With the state variables defined, 

A full run-through of the methodology behind the acquisition of the system's state equation can be seen [here](https://github.com/MECA482-ReactionWheel/InertiaWheel/blob/main/images/482%20wheel%20clacs.pdf).
## Sensor Calibration
## Controller Design Simulation
## Controller Implementation
## Appendix A: Simulation Code
## References


