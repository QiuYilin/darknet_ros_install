# darknet_ros install and prepare data
reference URL：
```
https://github.com/leggedrobotics/darknet_ros
https://zhuanlan.zhihu.com/p/42124636
https://www.cnblogs.com/tango1221/p/10084969.html
```
一、依赖
1.opencv



2.boost

sudo apt-get install libboost-all-dev


二、编译
1.需要向github账号上传SSH
```
git clone --recursive git@github.com:leggedrobotics/darknet_ros.git
```
如果是GPU版本要修改makefile
```
cd darnet_ros/darknet
gedit makefile
```
```
GPU=1
CUDNN=1
OPENCV=1(因为ros有opencv 这里改为0就不用另外再装opencv了)
OPENMP=1
```
加上
```
-gencode arch=compute_60,code=[sm_60,compute_60]（和显卡性能系数有关 这是1060的 https://developer.nvidia.com/cuda-gpus）
```
在该文件夹终端
```
make
```
```
cd catkin_ws/src/darknet_ros/

catkin_make -DCMAKE_BUILD_TYPE=Release
```





训练
见别的文档

使用
darknet文件夹的修改和训练时一致
修改权重
将自己的权重放到yolo_network_config/weights
将自己的配置文件放到yolo_network_config/cfg
修改launch file  <rosparam command="load" ns="darknet_ros" file="$(find darknet_ros)/config/yolov3_tinajin.yaml"/>

修改ros_yaml
修改network_param_file

