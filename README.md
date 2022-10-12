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
  setFixedSize(500, 500);
  setWindowTitle("MyTurtleSim");

  srand(time(NULL));
Return to first terminal where you ran colcon build earlier and run it again.
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
![Screenshot from 2022-10-12 22-08-41](https://user-images.githubusercontent.com/81208782/195354306-6c637f17-32b7-4d68-9862-759efca057d5.png)

# Create a package
```bash
# in this case i already have these files!
dostonbek@dostonbek-virtual-machine:~/ros2_ws/src$ ros2 pkg create --build-type ament_python --node-name my_node my_package

Aborted!
The directory already exists: ./my_package
Either remove the directory or choose a different destination directory or package name

# BUILDING PACKAGES
dostonbek@dostonbek-virtual-machine:~/ros2_ws$ colcon build --packages-select my_package
Starting >>> my_package
--- stderr: my_package                   
/usr/lib/python3/dist-packages/setuptools/command/install.py:34: SetuptoolsDeprecationWarning: setup.py install is deprecated. Use build and pip and other standards-based tools.
  warnings.warn(
---
Finished <<< my_package [5.72s]

Summary: 1 package finished [6.87s]
  1 package had stderr output: my_package

# Source the setup file
dostonbek@dostonbek-virtual-machine:~/ros2_ws$ . install/local_setup.bash

#Use the package
dostonbek@dostonbek-virtual-machine:~/ros2_ws$ ros2 run my_package my_node
Hi from my_package.

```

# Writing a publisher and subscriber(Python)
```bash
#MAKE SURE YOU ARE IN THE src FOLDER AND ENTER THE COMMAND FOR CREATING THE PY_PACKAGE
dostonbek@dostonbek-virtual-machine:~/ros2_ws/src$ ros2 pkg create --build-type ament_python py_pubsub
going to create a new package
package name: py_pubsub
destination directory: /home/dostonbek/ros2_ws/src
package format: 3
version: 0.0.0
description: TODO: Package description
maintainer: ['dostonbek <zeripboyevdostonbek@gmail.com>']
licenses: ['TODO: License declaration']
build type: ament_python
dependencies: []
creating folder ./py_pubsub
creating ./py_pubsub/package.xml
creating source folder
creating folder ./py_pubsub/py_pubsub
creating ./py_pubsub/setup.py
creating ./py_pubsub/setup.cfg
creating folder ./py_pubsub/resource
creating ./py_pubsub/resource/py_pubsub
creating ./py_pubsub/py_pubsub/__init__.py
creating folder ./py_pubsub/test
creating ./py_pubsub/test/test_copyright.py
creating ./py_pubsub/test/test_flake8.py
creating ./py_pubsub/test/test_pep257.py
.... 

# Write the publisher node
# Download the example talker code by entering the following command:
dostonbek@dostonbek-virtual-machine:~/ros2_ws/src/py_pubsub/py_pubsub$ wget https://raw.githubusercontent.com/ros2/examples/humble/rclpy/topics/minimal_publisher/examples_rclpy_minimal_publisher/publisher_member_function.py
--2022-10-12 22:48:59--  https://raw.githubusercontent.com/ros2/examples/humble/rclpy/topics/minimal_publisher/examples_rclpy_minimal_publisher/publisher_member_function.py
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.111.133, 185.199.109.133, 185.199.108.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.111.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1576 (1.5K) [text/plain]
Saving to: ‘publisher_member_function.py’

publisher_member_fu 100%[===================>]   1.54K  --.-KB/s    in 0.001s  

2022-10-12 22:48:59 (1.83 MB/s) - ‘publisher_member_function.py’ saved [1576/1576]

# Write the subscriber node
dostonbek@dostonbek-virtual-machine:~/ros2_ws/src/py_pubsub/py_pubsub$ wget https://raw.githubusercontent.com/ros2/examples/humble/rclpy/topics/minimal_subscriber/examples_rclpy_minimal_subscriber/subscriber_member_function.py
--2022-10-12 22:57:25--  https://raw.githubusercontent.com/ros2/examples/humble/rclpy/topics/minimal_subscriber/examples_rclpy_minimal_subscriber/subscriber_member_function.py
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.109.133, 185.199.108.133, 185.199.110.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.109.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1469 (1.4K) [text/plain]
Saving to: ‘subscriber_member_function.py’

subscriber_member_f 100%[===================>]   1.43K  --.-KB/s    in 0.001s  

2022-10-12 22:57:26 (1.23 MB/s) - ‘subscriber_member_function.py’ saved [1469/1469]

# Build and run
dostonbek@dostonbek-virtual-machine:~/ros2_ws$ rosdep install -i --from-path src --rosdistro humble -y
All required rosdeps installed successfully
# Still in the root of your workspace, ros2_ws, build your new package:
dostonbek@dostonbek-virtual-machine:~/ros2_ws$ colcon build --packages-select py_pubsub
Starting >>> py_pubsub
--- stderr: py_pubsub                   
/usr/lib/python3/dist-packages/setuptools/command/install.py:34: SetuptoolsDeprecationWarning: setup.py install is deprecated. Use build and pip and other standards-based tools.
  warnings.warn(
---
Finished <<< py_pubsub [5.65s]

Summary: 1 package finished [6.78s]
  1 package had stderr output: py_pubsub

---------------------------------------
# TESTING THE NODES
---------------------------------------
dostonbek@dostonbek-virtual-machine:~/ros2_ws$ . install/setup.bash
dostonbek@dostonbek-virtual-machine:~/ros2_ws$ ros2 run py_pubsub talker
[INFO] [1665583443.243800209] [minimal_publisher]: Publishing: "Hello World: 0"
[INFO] [1665583443.548757210] [minimal_publisher]: Publishing: "Hello World: 1"
[INFO] [1665583444.042925022] [minimal_publisher]: Publishing: "Hello World: 2"
[INFO] [1665583444.544386055] [minimal_publisher]: Publishing: "Hello World: 3"
[INFO] [1665583445.042098313] [minimal_publisher]: Publishing: "Hello World: 4"

 ----------------------------------------------------------------------------
 dostonbek@dostonbek-virtual-machine:~/ros2_ws$ . install/setup.bash
dostonbek@dostonbek-virtual-machine:~/ros2_ws$ ros2 run py_pubsub listener
[INFO] [1665583484.759161000] [minimal_subscriber]: I heard: "Hello World: 83"
[INFO] [1665583485.055122321] [minimal_subscriber]: I heard: "Hello World: 84"
[INFO] [1665583485.551994070] [minimal_subscriber]: I heard: "Hello World: 85"
[INFO] [1665583486.052137461] [minimal_subscriber]: I heard: "Hello World: 86"
 
```

# Writing a simple service and client (Python)
```bash
# Create a package
dostonbek@dostonbek-virtual-machine:~$ cd ros2_ws
dostonbek@dostonbek-virtual-machine:~/ros2_ws$ cd src
dostonbek@dostonbek-virtual-machine:~/ros2_ws/src$ ros2 pkg create --build-type ament_python py_srvcli --dependencies rclpy example_interfaces
going to create a new package
package name: py_srvcli
destination directory: /home/dostonbek/ros2_ws/src
package format: 3
version: 0.0.0
description: TODO: Package description
maintainer: ['dostonbek <zeripboyevdostonbek@gmail.com>']
licenses: ['TODO: License declaration']
build type: ament_python
dependencies: ['rclpy', 'example_interfaces']
creating folder ./py_srvcli
creating ./py_srvcli/package.xml
creating source folder
creating folder ./py_srvcli/py_srvcli
creating ./py_srvcli/setup.py
creating ./py_srvcli/setup.cfg
creating folder ./py_srvcli/resource
creating ./py_srvcli/resource/py_srvcli
creating ./py_srvcli/py_srvcli/__init__.py
creating folder ./py_srvcli/test
creating ./py_srvcli/test/test_copyright.py
creating ./py_srvcli/test/test_flake8.py
creating ./py_srvcli/test/test_pep257.py


# Write the service node inside the ros2_ws/src/py_srvcli/py_srvcli directory:
------------------------------------------------------------------------------
dostonbek@dostonbek-virtual-machine:~/ros2_ws/src/py_srvcli$ nano service_member_function.py
dostonbek@dostonbek-virtual-machine:~/ros2_ws/src/py_srvcli$ nano client_member_function.py

# Add an entry points into the setup.py to be able to run the servic&client nodes.
----------------------------------------------------------------------------------
dostonbek@dostonbek-virtual-machine:~/ros2_ws/src/py_srvcli$ nano setup.py
 entry_points={
        'console_scripts': ['service = py_srvcli.service_member_function:main',
        'client = py_srvcli.client_member_function:main',
        ],
    },
    
 # BUILD AND RUN
 dostonbek@dostonbek-virtual-machine:~/ros2_ws$ rosdep install -i --from-path src --rosdistro humble -y
#All required rosdeps installed successfully
dostonbek@dostonbek-virtual-machine:~/ros2_ws$ colcon build --packages-select py_srvcli
Starting >>> py_srvcli
--- stderr: py_srvcli                   
/usr/lib/python3/dist-packages/setuptools/command/install.py:34: SetuptoolsDeprecationWarning: setup.py install is deprecated. Use build and pip and other standards-based tools.
  warnings.warn(
---
Finished <<< py_srvcli [5.14s]

Summary: 1 package finished [6.23s]
  1 package had stderr output: py_srvcli

# Open a new terminal, navigate to ros2_ws, and source the setup files
----------------------------------------------------------------------
dostonbek@dostonbek-virtual-machine:~$ cd ros2_ws
dostonbek@dostonbek-virtual-machine:~/ros2_ws$ . install/setup.bash
dostonbek@dostonbek-virtual-machine:~/ros2_ws$ ros2 run py_srvcli service
[INFO] [1665587399.390394773] [minimal_service]: Incoming request
a: 2 b: 3

# Do the same thing for the client node
dostonbek@dostonbek-virtual-machine:~/ros2_ws$ ros2 run py_srvcli client 2 3
Package 'py_srvcli' not found
dostonbek@dostonbek-virtual-machine:~/ros2_ws$ . install/setup.bash
dostonbek@dostonbek-virtual-machine:~/ros2_ws$ ros2 run py_srvcli client 2 3
[INFO] [1665587399.512228776] [minimal_client_async]: Result of add_two_ints: for 2 + 3 = 5

```
