# semantic_voxblox
一.kimera_semantics  build
1.对‘google::LogMessageFatal::LogMessageFatal（xxxxx）’未定义的引用
编译版本选择c++14
（此外还可以考虑gcc版本）
2.fatal error: depth_image_proc/depth_traits.h:
sudo apt-get install ros-kinetic-image-proc
3.src/mav_voxblox_planning/voxblox_skeleton/src/io/skeleton_io.cpp:72:75: error: cannot convert ‘uint32_t* {aka unsigned int*}’ to ‘uint64_t*
在代码报错处修改uint32_t*为uint64_t*

4.error: expression cannot be used as a function
把括号改成=true=false；

ORB-SLAM3
直接编译ros时，可能会遇到找不到sophus/se3.h。
这是因为orbslam自带的sophus编译路径不在寻找范围，两个解决办法，一是重新安装sophus库，但这个方法要保证和eigen版本适配，否则很容易和eigen库冲突，报redefinition错，第二个方法是把orb-slam下编译好的sophus头文件放到usr/local/include下即可。

mav-planning
5.PluginlibFactory: The plugin for class ‘rviz_plugins/Goal3DTool‘ failed to load.
google rosrun something and source
