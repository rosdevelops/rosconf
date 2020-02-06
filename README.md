# rosconf
collection of exports used to simplify the cooperation of many robots in one ros network

## Setup

- clone repository into home folder
  ```sh
  cd && git clone https://github.com/rosdevelops/rosconf.git
  ```

- in your shell config (.bashrc, .zshrc, .fishrc or other...) add the following:
  ```sh
  ROS_MASTER=192.168.0.XX # replace XX with current master host
  source ~/rosconf/.rosrc
  ```

- source shell config again or re-open terminal to apply new changes

## Info

the following environment variables are added:

- `TURTLEBOT3_MODEL`
- `ROS_DISTRO`
- `ROS_HOSTNAME`
- `ROS_NAMESPACE` your namespace to use in the project
- `ROS_MASTER_URI` the roscore service address
- `COOP_SEARCHING_TOPIC` the global topic used when a robot searches a tag
- `COOP_REACHED_TOPIC` the global topic used when a robot reaches a tag

## Hint

Example code to use environment variables in a launch file:

```xml
<arg name="topic_search" default="$(env COOP_SEARCHING_TOPIC)"/>

...

<node pkg="mypackage" type="mynode" name="mynode">
  <param name="topic_search" value="$(arg topic_search)" />
  ...
```

Note that this can also be directly used:
```xml
<node pkg="mypackage" type="mynode" name="mynode">
  <param name="topic_search" value="$(env COOP_SEARCHING_TOPIC)" />
  ...
```
