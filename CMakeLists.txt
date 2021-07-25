cmake_minimum_required (VERSION 3.16.3)
project (tf_demo)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -g -std=c++11 -W")

link_directories(/home/lilin/source/tf_lib/lib/)
include_directories(
    tf_lib/include
    tf_lib/include/third_party
    tf_lib/include/third_party/eigen_archive)
add_executable(tf_demo  main.cc) 
target_link_libraries(tf_demo tensorflow_cc tensorflow_framework)