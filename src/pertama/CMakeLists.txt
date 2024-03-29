cmake_minimum_required(VERSION 3.8)
project(pertama)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(std_msgs REQUIRED)

add_executable(hello src/main.cpp)
add_executable(publish src/publisher.cpp)
add_executable(subscribe src/subscriber.cpp)  

# ament_target_dependencies(${PROJECT_NAME} rclcpp std_msgs)
# ament_target_dependencies(hello rclcpp std_msgs)
ament_target_dependencies(publish rclcpp std_msgs)
ament_target_dependencies(subscribe rclcpp std_msgs)




if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # comment the line when a copyright and license is added to all source files
  set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # comment the line when this package is in a git repo and when
  # a copyright and license is added to all source files
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

install(TARGETS
# ${PROJECT_NAME}
hello
publish
subscribe
DESTINATION lib/${PROJECT_NAME})

ament_package()
