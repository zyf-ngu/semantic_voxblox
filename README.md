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
3.orbslam3  ‘boost::archive未定义的引用 collect2: error: ld returned 1 exit status
find_package(Boost COMPONENTS system filesystem serialization REQUIRED)
include_directories(
${Boost_INCLUDE_DIRS}
)
target_link_libraries(${PROJECT_NAME}
${Boost_LIBRARIES}
)


mav-planning
5.PluginlibFactory: The plugin for class ‘rviz_plugins/Goal3DTool‘ failed to load.
google rosrun something and source

glog使用--alsologtostderr参数时报这个错误ERROR:unknown command line flag ‘alsologtostderr’

其实这个问题可以将--alsologtostderr换成GLOG_alsologtostderr=1就可以解决。
根本这个原因是glog默认依赖gflags。


jbox link: https://jbox.sjtu.edu.cn/l/U1AOYS
高翔分享ORBSLAM2_with_pointcloud_map安装问题总结
https://blog.csdn.net/c417469898/article/details/104631814


kimeravio_ros
1.fatal error: unsupported/Eigen/MatrixFunctions: No such file or directory
2./home/luo/opencv-3.4.0/opencv_contrib/modules/xfeatures2d/src/boostdesc.cpp:653:20: fatal error: boostdesc_bgm.i: 没有那个文件或目录#include "boostdesc_bgm.i"
https://blog.csdn.net/weixin_44570248/article/details/118630357
3.报错2：fatal error: opencv2/xfeatures2d/cuda.hpp: No such file or directory
类似的，对于以下报错，都可以通过查找文件解决nonfree.hpp
https://www.cnblogs.com/ZHJ0125/p/12904507.html

realsense:问题
If you see the following error

1.Err:XX http://realsense-hw-public.s3.amazonaws.com/Debian/apt-repo bionic InRelease                                   
  403  Forbidden [IP: 52.218.36.57 80]
[...]
E: Failed to fetch http://realsense-hw-public.s3.amazonaws.com/Debian/apt-repo/dists/bionic/InRelease  403  Forbidden [IP: 52.218.36.57 80]
E: The repository 'http://realsense-hw-public.s3.amazonaws.com/Debian/apt-repo bionic InRelease' is no longer signed.

Remove the offending APT repo and add the new secure repo with:

$ sudo add-apt-repository --remove "deb http://realsense-hw-public.s3.amazonaws.com/Debian/apt-repo bionic main" -u
$ sudo add-apt-repository "deb https://librealsense.intel.com/Debian/apt-repo bionic main" -u
https://forum.hello-robot.com/t/expired-ros-gpg-key-new-realsense-apt-repo/205


arm64配置
首先选择比较好的源，首选豆瓣源
pip install -i http://pypi.douban.com/simple/ --trusted-host pypi.douban.com pakege-name
不成功尝试换其它源
1.需要安装scipy=1.2.3,pip=20.3.4,protobuf>=3.8;ipyhon=5.10.0;matplotlib=2.1.1;numpy=1.16.6
1.需要依赖h5py=2.10.0/2.8.0,需要先安装hdf5，然后sudo apt install python-h5py
https://blog.csdn.net/lai_cheng/article/details/107515404
报错 https://blog.csdn.net/jingchenlin1996/article/details/87904587
不能解决则sudo apt install python-h5py
2.需要安装keras，依赖h5py，scipy等
3.安装tensorflow1.5 ，利用whl 
