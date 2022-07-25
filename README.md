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
1.直接编译ros时，可能会遇到找不到sophus/se3.h。
这是因为orbslam自带的sophus编译路径不在寻找范围，两个解决办法，一是重新安装sophus库，但这个方法要保证和eigen版本适配，否则很容易和eigen库冲突，报redefinition错，第二个方法是把orb-slam下编译好的sophus头文件放到usr/local/include下即可。
2.   /usr/bin/ld: CMakeFiles/RGBD.dir/src/ros_rgbd.cc.o: undefined reference to symbol '_ZN5boost6system15system_categoryEv'
    /usr/lib/x86_64-linux-gnu/libboost_system.so: error adding symbols: DSO missing from command line
    collect2: error: ld returned 1 exit status
    CMakeFiles/RGBD.dir/build.make:216: recipe for target '../RGBD' failed
    make[2]: *** [../RGBD] Error 1
    CMakeFiles/Makefile2:67: recipe for target 'CMakeFiles/RGBD.dir/all' failed
    make[1]: *** [CMakeFiles/RGBD.dir/all] Error 2
    make[1]: *** 正在等待未完成的任务....
    /usr/bin/ld: CMakeFiles/Stereo.dir/src/ros_stereo.cc.o: undefined reference to symbol '_ZN5boost6system15system_categoryEv'
    /usr/lib/x86_64-linux-gnu/libboost_system.so: error adding symbols: DSO missing from command line
    collect2: error: ld returned 1 exit status
    CMakeFiles/Stereo.dir/build.make:216: recipe for target '../Stereo' failed
    make[2]: *** [../Stereo] Error 1
    CMakeFiles/Makefile2:104: recipe for target 'CMakeFiles/Stereo.dir/all' failed
    make[1]: *** [CMakeFiles/Stereo.dir/all] Error 2
    [ 55%] Built target Mono
    [ 77%] Built target MonoAR
    Makefile:127: recipe for target 'all' failed
    make: *** [all] Error 2
找不到libboost文件，把系统自带的libboost-system.so，libboost-filesystem.so拷贝到orb-slam的lib文件下。
https://blog.csdn.net/qq_42703283/article/details/95969737

mav-planning
5.PluginlibFactory: The plugin for class ‘rviz_plugins/Goal3DTool‘ failed to load.
google rosrun something and source
