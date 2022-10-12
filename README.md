# Turtlism installation
## To make sure your system is up to date 
```bash
sudo apt update
```

## Install the turtlesim library
```bash
dostonbek@dostonbek-virtual-machine:~$ sudo apt install ros-humble-turtlesim
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
....
```

## Check that the package installed:
```bash
dostonbek@dostonbek-virtual-machine:~$ ros2 pkg executables turtlesim
turtlesim draw_square
turtlesim mimic
turtlesim turtle_teleop_key
turtlesim turtlesim_node
```

## To start turtlesim, enter the following command in your terminal:
```bash
dostonbek@dostonbek-virtual-machine:~$ ros2 run turtlesim turtlesim_node
[INFO] [1665564036.889087992] [turtlesim]: Starting turtlesim with node name /turtlesim
[INFO] [1665564036.927254550] [turtlesim]: Spawning turtle [turtle1] at x=[5.544445], y=[5.544445], theta=[0.000000]
```
![Screenshot from 2022-10-12 18-50-25](https://user-images.githubusercontent.com/81208782/195311932-0aa0343d-c0d0-4ce4-bd3c-e3df0bd60023.png)
## To control the turtle type the following command:
```bash 
dostonbek@dostonbek-virtual-machine:~$ ros2 run turtlesim turtle_teleop_key
Reading from keyboard
---------------------------
Use arrow keys to move the turtle.
Use G|B|V|C|D|E|R|T keys to rotate to absolute orientations. 'F' to cancel a rotation.
'Q' to quit.

```
# RQT: installation
```bash 
#  MAKE SURE YOUR SYSTEM IS UP-TO-DATE
dostonbek@dostonbek-virtual-machine:~$ sudo apt update

# INSTALL THE RQT LIBRARY AND ITS PLUGINS
dostonbek@dostonbek-virtual-machine:~$sudo apt install ~nros-humble-rqt*
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
...
# To run rqt by just typing command "rqt"
dostonbek@dostonbek-virtual-machine:~$ rqt
```
