Unity for ROS2
==============

![Turtebot3 Navigation2](https://i.gyazo.com/98d3d43aae3877593ecaefe4e5ba9a44.gif)

Build status
------------

| Target | Status |
|----------|--------|
| **Windows 10 Desktop**                  | [![Build status](https://ci.appveyor.com/api/projects/status/5hst1rj4hkjs54i9?svg=true)](https://ci.appveyor.com/project/samiamlabs/unity-ros2) |
| **Linux**                  | [![CircleCI](https://circleci.com/gh/DynoRobotics/unity_ros2.svg?style=svg)](https://circleci.com/gh/DynoRobotics/unity_ros2) |

Introduction
------------

This is a collection of projects (bindings, code generator, examples and more) for writing ROS2
applications for C# specificly targeted at Unity.

Platform support
----------------
This project curretly supports Windows 10 and Ubuntu 16.04. It should be possible to get it working on other systems as well.

Features
--------

The current set of features include:
- Generation of all builtin ROS types, dynamic arrays and nested types.
- Support for publishers and subscriptions
- Quality of service profiles
- Time (limited support)
- Importing robots from urdf
- Laser scan
- Tf publisher
- Pose publisher
- Tf subscriber/visualizer
- Odometry (ground truth, no noise yet)
- Base controller
- Joint controller interface (only position so far)
- Joint state publiser
- Distance sensor
- Navigation2 support
- Sending nav goals
- Sending navigation missions
- Path visualizer
- Keyboard teleop
- Tests
- and more...


What's missing?
---------------

Plenty of stuff!
- Clients and services
- Setting individual element of array in message (need to assign complete array atm.)
- Actions
- Documentation
- More examples
- Better cross-platform support (Windows IoT Core, UWP, Mac) [should work with minimal modifications, but not tested]
- Automatic test runner for CI (C#)
- Costmap visualizer
- Camera sensor
- 3d sensor
- Pointcloud visualizer
- Video visualiszer
- ros2_control support
- Hololens support

How can I try this out?
-----------------------
There are some prebuilt binaries available for this project that can make it easier to get started. If you want not use custom ROS2 messages from Unity you will need to build the project from source in order to generate c# libraries for them.

You need to install the standard ROS2 Crystal Clemmys dependencies for your operating system of choice https://index.ros.org/doc/ros2/Installation/
If you are building this project from source you will probably need to install the "from source" dependencies for ROS2 as well.

To build from source you will also need .Net Core https://www.microsoft.com/net/learn/get-started. On Windows 10 I recommend installing .NET via Visual Studio 2017.

Install Unity
https://forum.unity.com/threads/unity-hub-v-1-5-0-is-now-available.627847/

*NOTE: Tested with Unity 2018.3.6f1*

Tutorials
---------
https://unity-ros2.readthedocs.io

Installing
----------

The following steps describe how to install the example Unity/ROS2 project on Linux and Windows 10:

Linux
-----
### Using the prebuilt workspace

Download the latest archive for linux from [releases](https://github.com/DynoRobotics/unity_ros2/releases) 
Let’s assume that it ends up at `~/Downloads/standalone-unity-ws-0.0.1-beta-linux-xenial-amd64.tar.bz2`

```
cd ~
tar xf ~/Downloads/standalone-unity-ws-0.0.1-beta-linux-xenial-amd64.tar.bz2
```

### Building from source

```
mkdir -p ~/ros2_unity_ws/src
cd ~/ros2_unity_ws
wget https://github.com/DynoRobotics/unity_ros2/raw/master/ros2_unity.repos
vcs import src < ros2_unity.repos
colcon build --merge-install
source install/setup.bash
```

Now you can open this repository as a project in Unity and run the example scene that has a publisher and subscription.
The repository sould be located at ~/ros2_unity_ws/src/dotnet/unity_ros2 if you followed the instructions above.
Make sure you open Unity in a shell where you have sourced setup.bash so that the linker can find the C libraries.

Windows 10
----------
### Using the prebuilt workspace
Download the latest zip file for windows from [releases](https://github.com/DynoRobotics/unity_ros2/releases) 
Extract all to \dev\standalone_unity_ws
```
call \dev\standalone_unity_ws\install\local_setup.bat

```
### Building from source
```
md \dev\ros2_unity_ws\src
cd \dev\ros2_unity_ws
curl -sk https://github.com/DynoRobotics/unity_ros2/raw/master/ros2_unity.repos -o ros2_unity.repos
vcs import src < ros2_unity_win10.repos
call \dev\ros2\install\local_setup.bat
colcon build --merge-install
call install\setup.bash
```

Now you can open this repository as a project in Unity and run the example scene that has a publisher and subscription. Make sure you open Unity in a terminal with everything sourced, or to add inte bin and lib folders from both workspaces to PATH.
The repository sould be located at dev\ros2_unity_ws\src\dotnet\unity_ros2 if you followed the instructions above.
Make sure you open Unity in a shell where you have sourced setup.bash so that the linker can find the C libraries.



Example Applications
--------------------
[![Sweepbot](https://img.youtube.com/vi/eMKbbEQhBTg/0.jpg)](https://www.youtube.com/watch?v=nggGs9ZIdlk)
[![Package DropOff](https://img.youtube.com/vi/2is7kwPeydA/0.jpg)](https://www.youtube.com/watch?v=lptKRANOfCY)

