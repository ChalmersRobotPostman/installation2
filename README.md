* Download this [script](https://github.com/ChalmersRobotPostman/Installation.sh) , which downloads ROS, creates a new catkin workspace and clones down all the repositories you need. If you don't need to do all this, just comment out the lines you don't want to run.

    * Put the file where you want to create the new workspace and **source** it (just running it won't work)
     
          cd path/to/installation     

          source ./installation.sh

* Install and setup RosAria:

download the rosariainstallation file and run it from this aria webarchive:
		https://web.archive.org/web/20180205212122/http://robots.mobilerobots.com/wiki/Aria

* I
* How to run the robot with rviz: (this launch file will initiate with rotating two times) 
         roscore
	
         roslaunch p3dx_launch p3dx.launch
	
         rosrun rviz rviz

open the config through file -> open then go to catkin_ws/src/p3dx_launch/nav.rviz

* If you want to run the robot with keyboard, you can use rosaria_client: https://github.com/pengtang/rosaria_client

* A tutorial on how to record a map: https://github.com/fgrzeszc/p3dx_launch
Follow the steps under mapping, however we have made changes to the p3dx_launch file to work for our project.


* How to run apriltags-detection (this can be done simultaneously with running p3dx_launch
         rosrun apriltags2_ros ATtags_tt.py

* How to run the postman interface:
         roslaunch rosbridge_server rosbridge_websocket.launch

then, go into catkin_ws/src/POSTMAN_interface and start index.html. This will open the interface in a browser window.

this interface publishes string messages to the topic /goals, which the script interface_listener located in simple_navigation_goals/scripts uses to send position goals for the purpose of driving from the janitor's office in the edit building to balazs office.


* Install teamviewer, open terminal and run it by:
         teamviewer
then startup teamviewer on the tablet and connect.

* Configure navigation stack:

To tune the navigation stack, there are for .yaml files located in catkin_ws/src/p3dx_launch/nav_config where you can adjust parameters. Another way is to run rqt_reconfigure to adjust more parameters dynamically.

