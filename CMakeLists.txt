cmake_minimum_required (VERSION 3.16.3)
project (tf_demo)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g -std=c++11 -W")

SET(ENV{PKG_CONFIG_PATH} /usr/local/lib/pkgconfig)
FIND_PACKAGE(PkgConfig REQUIRED)
PKG_SEARCH_MODULE(PKG_OPENCV REQUIRED opencv)	#通过执行pkg-config程序，并指定我需要的模块是opencv,注意opencv名字固定，是源于安装OpenCV生成的opencv.pc，PKG_OPENCV是前缀(观察下面)，
												#eg: -- Checking for one of the modules 'opencv'

link_directories(/home/lilin/source/tf_lib/lib/)
include_directories(
    tf_lib/include
    tf_lib/include/third_party
    tf_lib/include/third_party/eigen_archive
    ${PKG_OPENCV_INCLUDE_DIRS})
add_executable(tf_demo  main.cc) 
target_link_libraries(tf_demo tensorflow_cc tensorflow_framework ${PKG_OPENCV_LDFLAGS})