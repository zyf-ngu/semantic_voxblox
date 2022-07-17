# semantic_voxblox
一.kimera_semantics  build
1.对‘google::LogMessageFatal::LogMessageFatal（xxxxx）’未定义的引用
编译版本选择c++14
（此外还可以考虑gcc版本）
2.fatal error: depth_image_proc/depth_traits.h:
sudo apt-get install ros-kinetic-image-proc
3.src/mav_voxblox_planning/voxblox_skeleton/src/io/skeleton_io.cpp:72:75: error: cannot convert ‘uint32_t* {aka unsigned int*}’ to ‘uint64_t*
在代码报错处修改uint32_t*为uint64_t*
