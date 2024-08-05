# TurtleSim-on-ROS
install and run the TurtleSim package on ROS (Robot Operating System). It also includes instructions for exploring topics, nodes, and services, and controlling the turtle using keyboard commands. 
### 1. Getting Started with Turtlesim
in Terminal

Start the roscore:

    $ roscore
To install and start the turtlesim:

    $ sudo apt-get install ros-$(rosversion -d)-turtlesim
Run turtlesim:

    $ rosrun turtlesim turtlesim_node

You will see this window

<img width="380" alt="tttt" src="https://github.com/user-attachments/assets/38bafefa-6c70-4316-af25-76f3995e1160">


### 2.Nodes
New in ROS hydro As of Hydro turtlesim uses the geometry_msgs/Twist message instead of its own custom one (turtlesim/Velocity in Groovy and older). Also the topic has been changed to cmd_vel (instead of command_velocity before).


#### 2.1 turtlesim_node
turtlesim_node provides a simple simulator for teaching ROS concepts.

#### 2.1.1 Subscribed Topics
    turtleX/cmd_vel (geometry_msgs/Twist)
The linear and angular command velocity for turtleX. The turtle will execute a velocity command for 1 second then time out. Twist.linear.x is the forward velocity, Twist.linear.y is the strafe velocity, and Twist.angular.z is the angular velocity.

#### 2.1.2 Published Topics
    turtleX/pose (turtlesim/Pose)
The x, y, theta, linear velocity, and angular velocity of turtleX.

#### 2.1.3 Services
a. clear 

    (std_srvs/Empty)

Clears the turtlesim background and sets the color to the value of the background parameters.

b. reset 
    
    (std_srvs/Empty)
Resets the turtlesim to the start configuration and sets the background color to the value of the background.

kill 

    (turtlesim/Kill)
Kills a turtle by name.

c. spawn 

    (turtlesim/Spawn)
Spawns a turtle at (x, y, theta) and returns the name of the turtle. Also will take name for argument but will fail if a duplicate name.

    turtleX/set_pen (turtlesim/SetPen)
Sets the pen's color (r g b), width (width), and turns the pen on and off (off).

    turtleX/teleport_absolute (turtlesim/TeleportAbsolute)
Teleports the turtleX to (x, y, theta).

    turtleX/teleport_relative (turtlesim/TeleportRelative)
Teleports the turtleX a linear and angular distance from the turtles current position.

#### 2.1.4 Parameters
    ~background_b 
(int, default: 255)
Sets the blue channel of the background color.

    ~background_g 
    (int, default: 86)
Sets the green channel of the background color.
    ~background_r 
    (int, default: 69)
Sets the red channel of the background color.

### 2.2 mimic
mimic provides a simple interface for making one turtlesim mimic another.

### 2.2.1 Subscribed Topics
    input (turtlesim/Pose)
The input topic for the mimic node. The topic must be remapped to the pose topic of the desired turtle to mimic.

#### 2.2.2 Published Topics
    output (geometry_msgs/Twist)
The output topic for the mimic node. The topic must be remapped to the cmd_vel topic of the mimicking turtle
