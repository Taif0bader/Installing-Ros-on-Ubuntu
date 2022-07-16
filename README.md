# Installing-Ros-on-Ubuntu

## step 1: Install VirtualBox
## step 2: Download Ubuntu version 16.04 LTS
## step 3: Create a new Virtual Machine
## step 4: Follow the required commands,copy and paste the commands in the Ubuntu Terminal

### 1.Setup the computer to accept software from packages.ros.org:
    ``` 
       sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
    ```
### 2.The following key should be added to Ubuntu before starting installation:
   ```
  sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
   ```
### 3.Update the list of packages on Ubuntu:
       ```
   sudo apt-get update
       ```
### 4.Install the entire ROS package suite using the following command:
       ```
       -sudo apt-get install ros-kinetic-desktop-full
       -apt-cache search ros-kinetic
       ```
       
### 5.Environment setup:
      ```
       echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc
       source ~/.bashrc
      ```
### 6.Install tools and other dependencies for building ROS packages:
      ```
       sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential
      ```
### 7.Initialize rosdep:
      ```
       -sudo apt install python-rosdep
       -sudo rosdep init 
       -rosdep update
      ```
### 8.Install catkin:
      ```
       sudo apt-get install ros-noetic-catkin
      ```
### 9.Make workspace:
      ```
       -mkdir -p ~/catkin_ws/src
       -cd ~/catkin_ws/
       -catkin_make
       -cd ~/catkin_ws/src
     ```
### 10.To can acsses packages of robot:
```
       -git clone https://github.com/smart-methods/arduino_robot_arm.git
       -cd ~/catkin_ws
       -rosdep install --from-paths src --ignore-src -r -y
       -sudo apt-get install ros-kinetic-moveit
       -sudo apt-get install ros-kinetic-joint-state-publisher ros-kinetic-joint-state-publisher-gui
       -sudo apt-get install ros-kinetic-gazebo-ros-control joint-state-publisher
       -sudo apt-get install ros-kinetic-ros-controllers ros-kinetic-ros-control
       -sudo nano ~/.bashrc
       -at the end of the (bashrc) file add the follwing line
        (source /home/SystemName/catkin_ws/devel/setup.bash)
        then 
       ctrl + o
       then
       ctrl + x

      -source ~/.bashrc

      -roslaunch robot_arm_pkg check_motors.launch
 ```
#### Now, Rviz program will open on Ros to work on robot arm
        
### last step of the installation process. Check which version of ROS you have installed. If you see your ROS version as the output, congratulations you have           successfully installed ROS!
```
- rosversion -d 
 ```     

