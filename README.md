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
![Screenshot from 2022-10-12 19-05-04](https://user-images.githubusercontent.com/81208782/195314607-a6f7c068-1cae-469c-af4c-232bd7b46e4c.png)

# RQT: running rqt_console
```bash
dostonbek@dostonbek-virtual-machine:~$ ros2 run rqt_console rqt_console
```

![Screenshot from 2022-10-12 19-09-14](https://user-images.githubusercontent.com/81208782/195315734-03b518b0-29c3-4aa6-845b-7bc656ef08ab.png)

### Turtlesim simulation
```bash  
# RUN THE TURTLESIM_NODE IN A NEW TAB
dostonbek@dostonbek-virtual-machine:~$ ros2 run turtlesim turtlesim_node
[INFO] [1665564036.889087992] [turtlesim]: Starting turtlesim with node name /turtlesim
[INFO] [1665564036.927254550] [turtlesim]: Spawning turtle [turtle1] at x=[5.544445], y=[5.544445], theta=[0.000000]
# RUN THE TURTLE_TELEOP_KEY TO MOVE THE TURTLE IN A NEW TAB
dostonbek@dostonbek-virtual-machine:~$ ros2 run turtlesim turtle_teleop_key
Reading from keyboard
---------------------------
Use arrow keys to move the turtle.
Use G|B|V|C|D|E|R|T keys to rotate to absolute orientations. 'F' to cancel a rotation.
'Q' to quit.
#RUN THE rqt in your terminal
dostonbek@dostonbek-virtual-machine:~$ rqt
#CHANGE THE /SPAWN SERVICE PARAMETERS TO RUN TURTLE2
#TO RUN THE TURTLE TO RUN THIS COMMAND
dostonbek@dostonbek-virtual-machine:~$ ros2 run turtlesim turtle_teleop_key --ros-args --remap turtle1/cmd_vel:=turtle2/cmd_vel
Reading from keyboard
---------------------------
Use arrow keys to move the turtle.
Use G|B|V|C|D|E|R|T keys to rotate to absolute orientations. 'F' to cancel a rotation.
'Q' to quit.
```
![Screenshot from 2022-10-12 19-20-46](https://user-images.githubusercontent.com/81208782/195318607-042bf0f5-5cae-4ff3-b92e-a91908675c1f.png)

# TURTLE simulation
[Screencast from 10-12-2022 07:26:28 PM.webm](https://user-images.githubusercontent.com/81208782/195319523-fb7dfc8c-0d0a-4a2f-aaad-b2da4afc42ac.webm)

## ROS2 Colcon
```bash 
# INSTALLING Colcon
dostonbek@dostonbek-virtual-machine:~$ sudo apt install python3-colcon-common-extensions
[sudo] password for dostonbek: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
python3-colcon-common-extensions is already the newest version (0.3.0-1).
The following package was automatically installed and is no longer required:
  systemd-hwe-hwdb
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.

-----------------------------------
 # ROS2 Colcon: Create a workspace
-----------------------------------
# Source ROS 2 environment
dostonbek@dostonbek-virtual-machine:~$ source /opt/ros/humble/setup.bash
# Create a new directory
dostonbek@dostonbek-virtual-machine:mkdir -p ~/ros2_ws/src cd ~/ros2_ws/src
# Clone a sample repo
dostonbek@dostonbek-virtual-machine:~/ros2_ws/src$ git clone https://github.com/ros/ros_tutorials.git -b humble-devel
Cloning into 'ros_tutorials'...
remote: Enumerating objects: 2841, done.
remote: Counting objects: 100% (161/161), done.
remote: Compressing objects: 100% (88/88), done.
remote: Total 2841 (delta 93), reused 131 (delta 71), pack-reused 2680
Receiving objects: 100% (2841/2841), 617.66 KiB | 3.06 MiB/s, done.
Resolving deltas: 100% (1710/1710), done.
# Resolve dependencies
dostonbek@dostonbek-virtual-machine:~/ros2_ws/src$ # cd if you're still in the ``src`` directory with the ``ros_tutorials`` clone
cd ..
rosdep install -i --from-path src --rosdistro humble -y
All required rosdeps installed successfully


# BUILD THE WORKSPACE WITH Colcon
 dostonbek@dostonbek-virtual-machine:~/ros2_ws$ colcon build
[0.829s] WARNING:colcon.colcon_core.package_selection:Some selected packages are already built in one or more underlay workspaces:
	'examples_rclpy_minimal_client' is in: /home/dostonbek/ros2_ws/install/examples_rclpy_minimal_client, /opt/ros/humble
	'examples_rclpy_minimal_service' is in: /home/dostonbek/ros2_ws/install/examples_rclpy_minimal_service, /opt/ros/humble
Finished <<< launch_testing_examples [4.63s]
Starting >>> turtlesim
--- stderr: my_package                                      
/usr/lib/python3/dist-packages/setuptools/command/install.py:34: SetuptoolsDeprecationWarning: setup.py install is deprecated. Use build and pip and other standards-based tools.
  warnings.warn(
---
Finished <<< my_package [3.06s]
[Processing: turtlesim]                               
[Processing: turtlesim]                                        
[Processing: turtlesim]                                         
[Processing: turtlesim]                                         
Finished <<< turtlesim [2min 27s]                                
                             
Summary: 24 packages finished [2min 53s]


# Source the overlay
dostonbek@dostonbek-virtual-machine:~/ros2_ws$ source /opt/ros/humble/setup.bash
dostonbek@dostonbek-virtual-machine:~/ros2_ws$ cd ~/ros2_ws
dostonbek@dostonbek-virtual-machine:~/ros2_ws$ . install/local_setup.bash

# Modify the overlay
You can modify turtlesim in your overlay by editing the title bar on the turtlesim window. To do this, locate the turtle_frame.cpp file in ~/ros2_ws/src/ros_tutorials/turtlesim/src. Open turtle_frame.cpp with your preferred text editor.

On line 52 you will see the function setWindowTitle("TurtleSim");. Change the value ”TurtleSim” to ”MyTurtleSim”, and save the file.
```cpp
  setFixedSize(500, 500);
  setWindowTitle("MyTurtleSim");

  srand(time(NULL));

```
- Return to first terminal where you ran colcon build earlier and run it again.
dostonbek@dostonbek-virtual-machine:~/ros2_ws$ colcon build
Finished <<< launch_testing_examples [12.3s]
Starting >>> turtlesim
--- stderr: my_package                                           
/usr/lib/python3/dist-packages/setuptools/command/install.py:34: SetuptoolsDeprecationWarning: setup.py install is deprecated. Use build and pip and other standards-based tools.
  warnings.warn(
---
Finished <<< my_package [7.72s]
[Processing: turtlesim]                                    
[Processing: turtlesim]                                        
[Processing: turtlesim]                                          
Finished <<< turtlesim [1min 33s]                             

Summary: 24 packages finished [3min 18s]




```

