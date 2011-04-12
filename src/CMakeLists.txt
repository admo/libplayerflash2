# find pkg-config
find_package(PkgConfig REQUIRED)

# check for Player/Stage C++ libraries
pkg_check_modules(playercore REQUIRED playercore)

# includes
include_directories(${playercore_INCLUDE_DIRS})

add_library(playerflash2 SHARED flash.cpp flashsip.cpp packet.cpp robot_params.cpp kinecalc.cpp)

target_link_libraries(playerflash2 ${playercore_LIBRARIES})

set_target_properties (playerflash2 PROPERTIES
  VERSION 0.0.1
  SOVERSION 0.0.1)

install (TARGETS playerflash2 DESTINATION lib COMPONENT libraries)

