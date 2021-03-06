

These packages are used to simulate the flying robot Ardrone in ROS environment using gazebo simulator. Totally they are 4 packages. Their functions are descript as below:

1. cvg_sim_gazebo: contains object models, sensor models, quadrocopter models, flying environment information and individual launch files for each objects and pure environment without any other objects.

2. cvg_sim_gazebo_plugins: contains gazebo plugins for the quadrocopter model. quadrotor_simple_controller is used to control the robot motion and deliver navigation information, such as: /ardrone/navdata. Others are plugins for sensors in the quadrocopter, such as: IMU sensor, sonar sensor, GPS sensor.

3. message_to_tf: is a package used to create a ros node, which transfers the ros topic /ground_truth/state to a /tf topic.

4. cvg_sim_msgs: contains message forms for the simulator.

Some packages are based on the tu-darmstadt-ros-pkg by Stefan Kohlbrecher, TU Darmstadt.


How to run a simulation:

1. Download all the required packages, include four packages above and ardrone_autonomy package (which contains some standard message forms for ardrone simulator).

2. Build packages cvg_sim_gazebo_plugins and message_to_tf.
    rosmake cvg_sim_gazebo_plugins
    rosmake message_to_tf

3. Start a ros master by typing the following command in console
    roscore

4. Run a simulation by executing a launch file in cvg_test_sim package:
    roslaunch cvg_sim_gazebo ardrone_testworld.launch

5. You can manipulate the quadrocopter in gazebo simulator by downloading the ardrone_helpers package and using a joy-stick after calling this command:
    roslaunch ardrone_joystick teleop.launch


Information for manipulation via joystick:

1. The L1 button starts the quadrocopter. It also works as a deadman button so that the robot will land if you release it during flight.

2. The left stick can be used to control the vx/vy-velocity. Keep in mind that these velocities are given in the local frame of the drone!

3. The right stick controls the yaw-rate and the altitude. 

4. The select button can be used to switch between the two cameras. This can also be done by executing rosservice call /ardrone/togglecam.


