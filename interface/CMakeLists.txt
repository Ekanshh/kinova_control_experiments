# Find required packages
find_package(orocos_kdl REQUIRED)
find_package(kdl_parser REQUIRED)
find_package(urdf REQUIRED)
find_library(libconfig libconfig)

add_library(kinova_control_interface INTERFACE)
target_link_libraries(kinova_control_interface INTERFACE kinova_api abag kinova_util config++ orocos-kdl kdl_parser urdf)