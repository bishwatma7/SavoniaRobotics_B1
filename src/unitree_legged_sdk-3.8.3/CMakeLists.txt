cmake_minimum_required(VERSION 2.8.3)
project(unitree_legged_sdk)

include_directories(include)
include_directories(./)

# add_compile_options(-std=c++11)
add_compile_options(-std=c++14)

# check arch and os
message("-- CMAKE_SYSTEM_PROCESSOR: ${CMAKE_SYSTEM_PROCESSOR}")
if("${CMAKE_SYSTEM_PROCESSOR}" MATCHES "x86_64.*")
  set(ARCH amd64)
endif()
if("${CMAKE_SYSTEM_PROCESSOR}" MATCHES "aarch64.*")
  set(ARCH arm64)
endif()

link_directories(lib/cpp/${ARCH})
set(EXTRA_LIBS -pthread libunitree_legged_sdk.so)

set(CMAKE_CXX_FLAGS "-O3 -fPIC")

# one pc one process
add_executable(example_position example/example_position.cpp)
target_link_libraries(example_position ${EXTRA_LIBS})

add_executable(front_left_hangup example/front_left_hangup.cpp)
target_link_libraries(front_left_hangup ${EXTRA_LIBS})

add_executable(fourleg_hangup example/fourleg_hangup.cpp)
target_link_libraries(fourleg_hangup ${EXTRA_LIBS})

add_executable(test1 example/test1.cpp)
target_link_libraries(test1 ${EXTRA_LIBS})

add_executable(test2 example/test2.cpp)
target_link_libraries(test2 ${EXTRA_LIBS})


add_executable(example_velocity example/example_velocity.cpp)
target_link_libraries(example_velocity ${EXTRA_LIBS})

add_executable(example_torque example/example_torque.cpp)
target_link_libraries(example_torque ${EXTRA_LIBS})

add_executable(example_walk example/example_walk.cpp)
target_link_libraries(example_walk ${EXTRA_LIBS})

add_executable(example_joystick example/example_joystick.cpp)
target_link_libraries(example_joystick ${EXTRA_LIBS})




