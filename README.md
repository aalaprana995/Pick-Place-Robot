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
The following steps are followed to get the final transformation matrix:
1) Assign each joint of the robot a frame using the rules for DH-Frame assignment.
2) Create DH-Tabel for all the joints, remenber the number of rows in a DH-Table is n-1 where "n" is the number of joints.
3) Fill the DH table with approriate values and using the transformation matrix given below find the tranformation for each joint.
![Forward_Kinematics_Matrix](https://user-images.githubusercontent.com/93336207/140411698-d62b2776-b235-40ef-8f07-f6e34cef7eef.gif)
4) Combine the trandformation to get the location at any joint / endeffector.


### Inverse Kinematics
Inverse kinematics is a mathematical process used to calculate the joint positions that are needed to place a robot’s end effector at a specific position and orientation (also known as its “pose”).\
In case of Baxter we cannot find Analytical Inverse Kinematic Solution, thus we make few simplifications ie we lock joint 3, consider the length l5 to be 0 and combine length l2.l3 to form a new length lh.
We now modify our angles and the forward kinematic transformation matrix. Now 0T6 is equivalent to 0T4 and on observation it is in terms of &#920;1,&#920;2 and &#920;4. Thus we can use 0T4 for calculatinhg them.\
**New Transformation matrix**

![Screenshot from 2021-11-07 17-40-42](https://user-images.githubusercontent.com/93336207/140664540-2ba72e8a-51b1-4b7e-aeea-bf1c5affc7f1.png)

![elbow](https://user-images.githubusercontent.com/93336207/140664541-8f2a6dcd-e4da-4b07-9ebe-6b1cb9b96ad4.png)

**&#920;1 Calculation**\
Using the translational components we can use y and x component to find &#920;1 :\
![Screenshot from 2021-11-07 17-38-33](https://user-images.githubusercontent.com/93336207/140664475-d2954ab4-199c-4ca6-91ff-4b918b7c2d79.png)

**&#920;2 Calculation and &#920;4 Calculation**\
Using  &#920;1 and z and x from the transformation matrix elbow.
![Screenshot from 2021-11-07 17-51-00](https://user-images.githubusercontent.com/93336207/140664868-aa876121-b26e-46cd-8349-3359d68588ae.png)
![Screenshot from 2021-11-07 17-53-19](https://user-images.githubusercontent.com/93336207/140664949-90db0bae-acb6-4b99-941a-e786d4ed906c.png)

**&#920;3 Calculation**\
It is assumed to be locked so 0

**&#920;5 Calculation , &#920;6 Calculation and &#920;7 Calculation**\
Using the rotational part of wrist matrix we can calculate all the angles\
![Screenshot from 2021-11-07 18-03-05](https://user-images.githubusercontent.com/93336207/140665189-c3806e5e-5872-454f-8dac-a4a3187504f2.png)
![Screenshot from 2021-11-07 17-58-26](https://user-images.githubusercontent.com/93336207/140665129-c11d1caf-9f61-4323-8f51-aa7b224ac441.png)


## Vrep Visualization
https://user-images.githubusercontent.com/93336207/139558479-d25b162e-7534-4f81-a971-b293c5c8e7e2.mp4

