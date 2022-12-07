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
接着继续根据Could not find a version that satisfies the requirement 安装包名字 查问题
会提示换成国内的pip源 可以解决问题

方法一：pip install 安装包名字 -i http://pypi.doubanio.com/simple/ --trusted-host pypi.doubanio.com //豆瓣镜像网站

方法二：pip install 安装包名字 -i http://pypi.douban.com/simple/ --trusted-host pypi.douban.com //豆瓣

方法三：pip install 安装包名字 -i https://pypi.tuna.tsinghua.edu.cn/simple/ --trusted-host pypi.tuna.tsinghua.edu.cn //清华大学

还有下面几个国内pip 源，大家可以依次按照上面的方法试下

1)http://mirrors.aliyun.com/pypi/simple/ 阿里云
2)https://pypi.mirrors.ustc.edu.cn/simple/ 中国科技大学
3) http://pypi.mirrors.ustc.edu.cn/simple/ 中国科学技术大学
1.需要安装scipy=1.2.3,pip=20.3.4,protobuf>=3.8;ipyhon=5.10.0;matplotlib=2.1.1;numpy=1.16.6
1.需要依赖h5py=2.10.0/2.8.0,需要先安装hdf5，然后sudo apt install python-h5py
https://blog.csdn.net/lai_cheng/article/details/107515404
报错 https://blog.csdn.net/jingchenlin1996/article/details/87904587
不能解决则sudo apt install python-h5py
2.需要安装keras，依赖h5py，scipy等
3.安装tensorflow1.5 ，利用whl https://github.com/lhelontra/tensorflow-on-arm/releases?page=2
tensorflow whl文件下载网址（贼快）
   一、 tensorflow whl文件下载网址：

    1、 https://www.lfd.uci.edu/~gohlke/pythonlibs/ ，网站里有很多python扩展库，但是tensorflow目前最新版本是1.9.0，而我需要的是2.3以上。

　 2、https://pypi.org/project/tensorflow-cpu/#history；CPU版本，自己选择版本平台，但是下载速度太慢了。

     3、https://pypi.org/project/tensorflow/#history；完整版本，自己选择版本平台，下载速度同上。

     4、https://pypi.tuna.tsinghua.edu.cn/simple/tensorflow-cpu/；CPU版本，自己选择版本平台，下载速度可以接受。

     5、https://pypi.tuna.tsinghua.edu.cn/simple/tensorflow/；完整版本，自己选择版本平台，下载速度同上。

     6、https://pub.mirrors.aliyun.com/pypi/simple/tensorflow-cpu/；CPU版本，自己选择版本平台，下载速度快。

　 7、https://pub.mirrors.aliyun.com/pypi/simple/tensorflow/；完整版本，自己选择版本平台，下载速度快。

     8、https://storage.googleapis.com/tensorflow/windows/cpu/tensorflow_cpu-2.3.4-cp36-cp36m-win_amd64.whl；CPU版本，大招，贼快，这才是正确的下载姿势，但是要自己改网址下载对应平台版本。

     9、https://storage.googleapis.com/tensorflow/windows/gpu/tensorflow-2.3.4-cp36-cp36m-win_amd64.whl；完整版本，下载速度同上，同理也要自己改网址下载对应平台版本。

     反正我是选最下面两个下载，太快了！！！

 

   二、tensorboard whl文件下载网址：

     tensorboard,pip有时也会卡死，下载也是奇慢，选择  https://pypi.tuna.tsinghua.edu.cn/simple/tensorboard/ 下载，1秒钟搞定。
     
     
   1。  ImportError: No module named request的解决方法
     （1）改为from six.moves.urllib import request
     环境用的是python 2.7，貌似python3.X的童鞋也会遇到代码中用了import urllib.request 和response = urllib.request.urlopen(url) 后通常会报以下错：

查询了C:\Users\Python27\Lib下的urllib moudle源码，并没有发现request方法，直接是urlopen方法，

    因此解决办法为：import urllib.request 改成import urllib

                                response= urllib.request.urlopen(url) 改成 

                                response= urllib.urlopen(url)   即可
                                
2。mask-rcnn 不显示检测后的图片，只输出原图
https://blog.csdn.net/qq_29227653/article/details/88414052
