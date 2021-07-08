# ROS, Qt5, PCL, VTK setting guide

* OS - Ubuntu 18.04 LTS

## Default setting

```
$ sudo apt-get update
$ sudo apt-get install build-essential libcurl4-openssl-dev curl git git-core libtool pkg-config autoconf automake
$ sudo apt-get install net-tools iputils-ping wget tcpdump libssl-dev
$ sudo apt-get install cmake libglfw3-dev libglew-dev libeigen3-dev libjsoncpp-dev libtclap-dev
```

## ROS install

1. Setup sources.list
```
$ sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```

2. Set up keys
```
$ sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
```
* Alternatively, use curl instead of the apt-key command
```
$ curl -sSL 'http://keyserver.ubuntu.com/pks/lookup?op=get&search=0xC1CF6E31E6BADE8868B172B4F42ED6FBAB17C654' | sudo apt-key add -
```

3. Installation ROS
```
$ sudo apt update
$ sudo apt install ros-melodic-desktop-full
```

4. Install ROS-Qt
```
$ sudo apt-get install ros-melodic-qt-create
$ sudo apt-get install ros-melodic-qt-build
```

* Create workspace example
```
$ source /opt/ros/melodic/setup.bash
$ mkdir -p ${workspace}/src
$ cd ${workspace}/src
$ catkin_create_pkg ${pkg_name} qt_build pcl_ros roscpp sensor_msgs std_msgs
```
* Modify CMakeLists.txt - refer to init_cmake_build/CMakeLists.txt
```
$ cd ${workspace}
$ catkin_make
```
* binary is to be placed on devel/lib/${pkg_name}
