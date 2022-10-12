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

##Check that the package installed:
```bash
dostonbek@dostonbek-virtual-machine:~$ ros2 pkg executables turtlesim
turtlesim draw_square
turtlesim mimic
turtlesim turtle_teleop_key
turtlesim turtlesim_node
```

##To start turtlesim, enter the following command in your terminal:
```bash
dostonbek@dostonbek-virtual-machine:~$ ros2 run turtlesim turtlesim_node
[INFO] [1665564036.889087992] [turtlesim]: Starting turtlesim with node name /turtlesim
[INFO] [1665564036.927254550] [turtlesim]: Spawning turtle [turtle1] at x=[5.544445], y=[5.544445], theta=[0.000000]
```
