cmake_minimum_required(VERSION 2.8.3)
project(CAD2pointcloud)


find_package(OpenCV REQUIRED)
find_package(PCL 1.6 REQUIRED)
 

find_package(catkin REQUIRED COMPONENTS
  tf
  tf2
  geometry_msgs
  roscpp
  rospy
  sensor_msgs
  std_msgs
  image_transport
  cv_bridge
)


catkin_package(
 
  CATKIN_DEPENDS geometry_msgs roscpp rospy sensor_msgs std_msgs 
 
)

include_directories(${CMAKE_CURRENT_LIST_DIR}/include)


include_directories(
  ${catkin_INCLUDE_DIRS}
 include

)


include_directories(${PCL_INCLUDE_DIRS})
link_directories(${PCL_LIBRARY_DIRS})
add_definitions(${PCL_DEFINITIONS})

 
add_executable(
CAD2pointcloud_node 

src/main.cpp
src/CAD2pointcloud_transformation.cpp
 
)


target_link_libraries(
CAD2pointcloud_node  

${catkin_LIBRARIES}
${OpenCV_LIBS}
${PCL_LIBRARIES}
)

 
