cmake_minimum_required( VERSION 3.1 )

project( glfw_project )

find_package( OpenGL REQUIRED )
include_directories( ${OPENGL_INCLUDE_DIRS} )

set( GLFW_SOURCE_DIR "${PROJECT_SOURCE_DIR}/glfw" )
include_directories("${GLFW_SOURCE_DIR}/deps")


set(GLAD_GL "${GLFW_SOURCE_DIR}/deps/glad_gl.c")
 
set( GLFW_BUILD_DOCS OFF CACHE BOOL  "GLFW lib only" )
set( GLFW_INSTALL OFF CACHE BOOL  "GLFW lib only" )
#set( GLFW_BUILD_EXAMPLES OFF CACHE BOOL "no example")
set( GLFW_BUILD_TESTS OFF CACHE BOOL "no test")

add_subdirectory( glfw )

set( GLFW-PROJECT-SRC
     main.cpp
     ${GLAD_GL}
     )
add_executable( glfw_project WIN32 ${GLFW-PROJECT-SRC} )
target_link_libraries( glfw_project ${OPENGL_LIBRARIES} glfw )
