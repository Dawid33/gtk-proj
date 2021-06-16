cmake_minimum_required(VERSION 3.0.0)
set(CMAKE_EXPORT_COMPILE_COMMANDS 1)

project(cpp_game)

include(CMakePrintHelpers)
include(FindPkgConfig)
find_package(PkgConfig REQUIRED)
pkg_check_modules(GTKMM REQUIRED gtkmm-4.0)
file(GLOB SOURCES "src/*.cpp")



add_executable(game ${SOURCES})
#target_include_directories(game PRIVATE "src/include")
target_include_directories(game PRIVATE ${GTKMM_INCLUDE_DIRS})
#target_compile_definitions(game PRIVATE ${GTKMM_CFLAGS_OTHER})
target_link_directories(game PRIVATE ${GTKMM_LIBRARY_DIRS})
target_link_libraries(game PRIVATE ${GTKMM_LIBRARIES})