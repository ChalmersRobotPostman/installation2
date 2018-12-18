* Download this [script](https://github.com/ChalmersRobotPostman/Installation.sh) (updated 2018-01-22), which downloads ROS, creates a new catkin workspace and clones down all the repositories you need. If you don't need to do all this, just comment out the lines you don't want to run

    * Put the file where you want to create the new workspace and **source** it (just running it won't work)
     
          cd path/to/installation     

          source ./installation.sh

* Install and setup RosAria:

Then, download the installation file from: 
		https://web.archive.org/web/20180205212122/http://robots.mobilerobots.com/wiki/Aria


### How to run the simulator ###
* `roslaunch truck_master master.launch`
* Use the "2D Nav Goal" tool to set the goal.
    * Watch as the pathplanning does it's thing and the truck starts to move :)
* To set the position and direction of the truck, use the "2D Pose Estimate" tool

