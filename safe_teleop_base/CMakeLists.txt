cmake_minimum_required(VERSION 2.8.3)
project(safe_teleop_base)

find_package(catkin REQUIRED COMPONENTS
  roscpp base_local_planner costmap_2d)
find_package(PCL REQUIRED)

catkin_package(
  CATKIN_DEPENDS roscpp base_local_planner costmap_2d
  DEPENDS pcl)

include_directories(include ${catkin_INCLUDE_DIRS} ${PCL_INCLUDE_DIRS})
add_executable(safe_teleop_base src/safe_trajectory_planner_ros.cpp src/safe_trajectory_planner.cpp)
target_link_libraries(safe_teleop_base ${catkin_LIBRARIES} ${PCL_LIBRARIES})

install(DIRECTORY include/${PROJECT_NAME}/
  DESTINATION ${CATKIN_PACKAGE_INCLUDE_DESTINATION})

install(TARGETS safe_teleop_base
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
  )
