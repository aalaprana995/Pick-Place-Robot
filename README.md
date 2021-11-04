# Pick-Place-Robot
This repository covers a project in robot kinematics. In this repository we display a way to use robot kinematics to do pick and place task.
## Project Objectives
- In this project kinematics equations including forward kinematic equations, inverse kinematic equations and
velocity kinematics equation would be manually calculated for a 7 degree of freedom robot namely, Baxter.
- The calculated equations would be validated through simulation in V-rep (robot simulation environment). 
- Using the kinematic concepts mentioned we would design a Collaborative Robotics Conveyor System to pick and place object to the desired location avoiding collision with obstacles.
## Why Baxter Robot
- There are several industrial robots which are capable for doing the pick and place or packaging task in the industry, but they are costly. Whereas, Baxter on the other side is about 4 times less expensive (due to its plastic body) which makes it affordable even for small to medium businesses.
- Baxter can be easily installed in human-occupied environment.
- Baxter can be reprogrammed to perform different tasks even by a non technical worker.
- It can adapt to the surrounding quickly.
## Project Assumptions
1. All the joints and objects are considered to be rigid.
2. External disturbances are not taken into account while modeling.
3. There is no (inverse kinematic )analytical solution for general 7 dof Baxter arm with
nonzero offset. Thus, we lock the joint angle θ 3 to 0 and assumed link lengths L 5 to
be 0 to obtain a solution.
4. The path generated using path planner is just one solution among the infinite possible scenarios and may not be the optimal solution.
5. Robot self collision is not considered i.e. collision with obstacle is only taken under
consideration for the scope of this project.
6. The Path Planning module is not available in the V-rep version and thus, path planning is done using forward kinematics by selection of appropriate way points.
## Forward Kinematics
### What is Forward Kinematics?
Forward kinematics refers to the use of the kinematic equations of a robot to compute the position of the end-effector from specified values for the joint parameters.
### Axsis Assignment
Assigning  Z axsis
![Screenshot from 2021-11-04 16-18-31](https://user-images.githubusercontent.com/93336207/140413715-f2085558-3850-488c-b1b3-62a08349a82a.png)


Assigning X axsis\
![Screenshot from 2021-11-04 16-14-33](https://user-images.githubusercontent.com/93336207/140413475-2ee7c825-7154-4502-99f9-3ff90a238075.png)
 

### DH-Parameter Method
We have used DH Parameter Method it is a shortcut for finding homogeneous transformation matrices.\
The following steps are followed to get the final transformation matrix:\
1) Assign each joint of the robot a frame using the rules for DH-Frame assignment.
2) Create DH-Tabel for all the joints, remenber the number of rows in a DH-Table is n-1 where "n" is the number of joints.
3) Fill the DH table with approriate values and using the transformation matrix given below find the tranformation for each joint.
![Forward_Kinematics_Matrix](https://user-images.githubusercontent.com/93336207/140411698-d62b2776-b235-40ef-8f07-f6e34cef7eef.gif)
4) Combine the trandformation to get the location at any joint / endeffector.


### Inverse Kinematics

## Vrep Visualization
https://user-images.githubusercontent.com/93336207/139558479-d25b162e-7534-4f81-a971-b293c5c8e7e2.mp4

