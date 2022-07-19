### First task:

### Installing-Ros-on-Ubuntu

### step 1: Install VirtualBox
### step 2: Download Ubuntu version 16.04 LTS
### step 3: Create a new Virtual Machine
### step 4: Follow the required commands,copy and paste the commands in the Ubuntu Terminal

#### 1.Setup the computer to accept software from packages.ros.org:
   ``` 
   sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
   ```
#### 2.The following key should be added to Ubuntu before starting installation:
   ```
  sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
   ```
#### 3.Update the list of packages on Ubuntu:
   ```
   sudo apt-get update
   ```
#### 4.Install the entire ROS package suite using the following command:
   ```
       -      sudo apt-get install ros-kinetic-desktop-full
       -      apt-cache search ros-kinetic
   ```
       
#### 5.Environment setup:
   ```
       echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc
       source ~/.bashrc
   ```
#### 6.Install tools and other dependencies for building ROS packages:
   ```
       sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential
   ```
#### 7.Initialize rosdep:
   ```
       -     sudo apt install python-rosdep
       -     sudo rosdep init 
       -     rosdep update
   ```
#### (Optional)
#### 8.Install catkin:
   ```
       sudo apt-get install ros-noetic-catkin
   ```
#### 9.Make workspace:
   ```
       -     mkdir -p ~/catkin_ws/src
       -     cd ~/catkin_ws/
       -     catkin_make
       -     cd ~/catkin_ws/src
   ```
#### 10.To can acsses packages of robot:
```
       -     git clone https://github.com/smart-methods/arduino_robot_arm.git
       -     cd ~/catkin_ws
       -     rosdep install --from-paths src --ignore-src -r -y
       -     sudo apt-get install ros-kinetic-moveit
       -     sudo apt-get install ros-kinetic-joint-state-publisher ros-kinetic-joint-state-publisher-gui
       -     sudo apt-get install ros-kinetic-gazebo-ros-control joint-state-publisher
       -     sudo apt-get install ros-kinetic-ros-controllers ros-kinetic-ros-control
       -     sudo nano ~/.bashrc
       -     at the end of the (bashrc) file add the follwing line
             (source /home/SystemName/catkin_ws/devel/setup.bash)
        then 
             ctrl + o
       then
            ctrl + x

      -     source ~/.bashrc

      -     roslaunch robot_arm_pkg check_motors.launch
 ```
#### Now, Rviz program will open on Ros to work on robot arm
        
#### last step of the installation process. Check which version of ROS you have installed. If you see your ROS version as the output, congratulations you have           successfully installed ROS!
```
- rosversion -d 
 ```     


## Task 2:


## installing Ros on Jetson nano:

#### step 1 : download XUbuntu 20.04 Jetson nano
#### step 2 : download balena Program to flash SD card:
#### step 3 : after the image download is complete , burn it on the SD card 
#### step 4 : Launch Etcher and select the XUbuntu image 
#### step 5 :Select the target SD card
#### step 6 : This will start burning the image
#### step 7 : when done, remove the SD and connect it to Ubuntu 
#### step 8: on Ubuntu select the SD card and open it with the file manger
#### step 9 : Open Boot folder 
#### step 10 : Open extlinux folder
#### step 11 : Choose to open terminal from that location 
#### step 12 :search b00.dbt file then copy file name 
#### step 13: cd extlinux
#### step 14 : sudo gedit extlinux.conf then open extlinux.conf
#### step 15 : type FDT/boot in LABEL primary And paste dtb fail name
#### step 16 : Save and quit 
#### step 17 :  Eject SD card from Ubuntu system
#### step 18 :  insert SD card on Jetson nano then Boot on Jetson nano
#### step 19 :  Fowllo steps of install ubuntu then Booting process will complete
```
          Luanch terminal then write :
          sudo apt install net-tools
          chack IP address using command ifconfig
          sudo apt install ssh
          Luanch terminal on my PC 
          ssh<Name of Jetson nano>@<Jetson nano IP>
  ```        
#### step 20  :Copy and paste the fowlloing commades to install Ros2 Foxy:
#####   Set locale:
```
    sudo apt update && sudo apt install locales
    sudo locale-gen en_US en_US.UTF-8
    sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
    export LANG=en_US.UTF-8
```
#####  Setup Sources:
```
   apt-cache policy | grep universe
```

#####  add the ROS 2 apt repository to your system.:
```
    sudo apt update && sudo apt install curl gnupg2 lsb-release
    sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key  -o /usr/share/keyrings/ros-archive-keyring.gpg
```

#####  Then add the repository to your sources list.:
```
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(source /etc/os-release &&     echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```
#####  Install ROS 2 packages:
###### Update your apt repository caches after setting up the repositories.
```
   sudo apt update
```
###### ensure your system is up to date before installing new packages.:
```
    sudo apt upgrade
```
#####  Desktop Install:
```
    sudo apt install ros-foxy-desktop
```
#####  ROS-Base Install :
```
   sudo apt install ros-foxy-ros-base
```
#####  Environment setup:
```
    source /opt/ros/foxy/setup.bash
```
### (Optional)
#####  Try some examples:
In one terminal, source the setup file and then run a C++ talker:
```
    source /opt/ros/foxy/setup.bash
    ros2 run demo_nodes_cpp talker
```
###### In another terminal source the setup file and then run a Python listener:
```
   source /opt/ros/foxy/setup.bash
   ros2 run demo_nodes_py listener
```
###### should see the talker saying that it’s Publishing messages and the listener saying I heard those messages.


