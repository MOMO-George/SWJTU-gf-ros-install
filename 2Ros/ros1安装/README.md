## 安装ros1：

```bash
https://wiki.ros.org/noetic/Installation/Ubuntu #官方Ubuntu安装网站
sudo sh -c '. /etc/lsb-release && echo "deb http://mirrors.ustc.edu.cn/ros/ubuntu/ `lsb_release -cs` main" > /etc/apt/sources.list.d/ros-latest.list'#切换中科大镜像。
sudo apt install curl #这个是安装的签名，以后有问题找这个更新。
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
sudo apt update
sudo apt install ros-noetic-desktop-full#至此ros1的主体部分都装完了，开始环境配置
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc#这个直接写入bashrc中了，如果后面有需要ros2，及时把这个注释应该就行
#安装rosdep，安装依赖包。
sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential #可以看到安装的是python和cmake的东西
sudo rosdep init#注意，网络问题就切换手机热点，校园网是这样的
rosdep update
#至此，ros1的所有安装结束，恭喜你，成功安装，祝你好运，RCer！
#以下是可选内容，通过ros1进行小乌龟的控制
sudo apt install ros-noetic-rqt-robot-steering 
roscore
rosrun rqt_robot_steering rqt_robot_steering #控制速度
sudo apt install ros-noetic-turtlesim #经典小乌龟
rosrun turtlesim turtlesim_node #小乌龟启动
#再将发布的消息名称改为turtle1/cmd_vel，即可完成对乌龟的控制
```
