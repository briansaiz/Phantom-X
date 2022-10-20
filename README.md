# Phantom-X
Repositoty for practices with a Phantom-X using the laptop keyboard and ROS .

> ## Contributors
> 
> - [Camilo Andrés Borda Gil](https://github.com/Canborda) (caabordagi@unal.edu.co)
> - [Brian Camilo Saiz Cavanzo](https://github.com/briansaiz) (brcsaizca@unal.edu.co)


## Cinematic analysis of the robot
The first step was take the measurements of the Phantom in the laboratory, obtaining the following results:
 - L1 = 145 [mm]
 - L2 = 107 [mm]
 - L3 = 107 [mm]
 - L4 = 80 [mm]

Then the reference systems are assigned according to the DHstd convention. 

<p align="center"><img height=700 src="./assets/Taller4_2022.png" alt="Phantom-X - DH Model" /></p>

Obtaining the following DH Parameters:

<p align="center"><img height=200 src="./assets/DHParemeters.PNG" alt="Phantom-X - DH Model" /></p>

## Cinematic analysis of the robot with MATLAB
With the Toolbox of MATLAB and the previously found DH Parameter, a SerialLink object was created as follows

```matlab
l=[145,107,107,80];  %[mm]
offset = [0 pi/2 0 0];
L(1) = Link('revolute','alpha',pi/2,'a', 0  ,'d',l(1),'offset',offset(1));
L(2) = Link('revolute','alpha',0,   'a',l(2),'d',0   ,'offset',offset(2));
L(3) = Link('revolute','alpha',0,   'a',l(3),'d',0   ,'offset',offset(3));
L(4) = Link('revolute','alpha',0,   'a',l(4),'d',0   ,'offset',offset(4));
Robot2=SerialLink(L,'name','R2')
```
Achieving the following DH parameters

<p align="center"><img height=700 src="./assets/DHParemeters2.PNG" alt="Phantom-X - DH Model" /></p>
