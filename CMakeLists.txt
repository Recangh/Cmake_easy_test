cmake_minimum_required(VERSION 3.28.3)
project(CMAKE_EASY_TEST)
set(CMAKE_CXX_STANDARD 11)

#变量和目录设置
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)   #动态库和exe文件都指定到这个目录下
#CMAKE_LIBRARY_OUTPUT_DIRECTORY Linux平台用这个
#CMAKE_ARCHIVE_OUTPUT_DIRECTORY 静态库输出目录

aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC_LIST)
add_library(common
SHARED
${SRC_LIST}
)

target_include_directories(common
PUBLIC
${PROJECT_SOURCE_DIR}/include
)


#可执行文件设置
add_executable(planning_main planning_main.cpp)

target_include_directories(planning_main
PUBLIC
${PROJECT_SOURCE_DIR}/include
)


#链接
target_link_libraries(planning_main
PUBLIC
common
)