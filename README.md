* This project was made on Ubuntu 16.04.01, following is a tutorial how to setup this up. This tutorial is brief, therefore you might have to you use google for certain parts.

* Download this [script](https://github.com/ChalmersRobotPostman/Installation.sh) , which downloads ROS, creates a new catkin workspace and clones down all the repositories you need. If you don't need to do all this, just comment out the lines you don't want to run. 

    * Put the file where you want to create the new workspace and **source** it (just running it won't work)
     
          cd path/to/installation     

          source ./installation.sh

* In this project, we followed this tutorial https://github.com/fgrzeszc/p3dx_launch, however a lot of adjustments had to be made to make it work along with our own packages.

* Install and setup RosAria:

First, download rosaria into catkin_ws/src:

        git clone https://github.com/amor-ros-pkg/rosaria.git

download the rosaria installation file from this aria webarchive and install install it with e.g. the ubuntu software center:

        https://web.archive.org/web/20180205212122/http://robots.mobilerobots.com/wiki/Aria


* The first time you connect the robot and the lidar to usb-ports, you might have to run
         
         sudo chmod a+rw /dev/ttyUSB0

         sudo chmod a+rw /dev/ttyACM0

to give permission for the user to use these.

* How to run the robot with rviz: (this launch file will initiate with rotating two times to try to localize itself) 

First, connect the lidar sensor, web-camera and the serial cable to the onboard computer, then run:

         roscore
	
         roslaunch p3dx_launch p3dx.launch
	
         rosrun rviz rviz

open the navigation config through file -> open then go to catkin_ws/src/p3dx_launch/nav.rviz (this can then next time be opened through file -> recent configs

* If you want to run the robot with keyboard, you can use rosaria_client: https://github.com/pengtang/rosaria_client

* A tutorial on how to record a map: https://github.com/fgrzeszc/p3dx_launch
Follow the steps under mapping, however we have made changes to the p3dx_launch file to work for our project.

* How to run apriltags-detection: (this can be done simultaneously with running p3dx.launch)

before running this the first time, you need to make the file executable by cd into catkin_ws/src/apriltags2_ros/apriltags2_ros/launch and then running

         chmod +x ATtags_test.py

then, to run the script:
 
         rosrun apriltags2_ros ATtags_test.py


this script is continously searching for certain tag id:s and then publishes a string message to the topic 'QRcode'. You can change the ID:s in the script, but the you need to add it aswell in the tags.yaml file located in catkin_ws/src/apriltags2_ros/apriltags2_ros/config. You can find more info about apriltags2 at: http://wiki.ros.org/apriltags2_ros/Tutorials/Detection%20in%20a%20video%20stream

* How to run the postman interface:

         roslaunch rosbridge_server rosbridge_websocket.launch

then, go into catkin_ws/src/POSTMAN_interface and start index.html. This will open the interface in a browser window.

this interface publishes string messages to the topic /goals, which the script interface_listener located in simple_navigation_goals/scripts uses to send position goals for the purpose of driving from the janitor's office in the edit building to balazs office.


* Install teamviewer, open terminal and run it by:

         teamviewer
then startup teamviewer on the tablet and connect.


* Configure navigation stack:

To tune the navigation stack, there are four .yaml files located in catkin_ws/src/p3dx_launch/nav_config where you set certain parameters. Another way is to run rqt_reconfigure to adjust more parameters dynamically.

