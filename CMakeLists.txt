# ┌──────────────────────────────────────────────────────────────────┐
# │  Projects Settings                                               │
# └──────────────────────────────────────────────────────────────────┘

cmake_minimum_required( VERSION 3.2.2 )
project(Simple3DEngine)
# ┌──────────────────────────────────────────────────────────────────┐
# │  Load libraries                                                  │
# └──────────────────────────────────────────────────────────────────┘
#glfw
set(GLFW_BUILD_EXAMPLES OFF CACHE STRING "" FORCE)
set(GLFW_BUILD_TESTS    OFF CACHE STRING "" FORCE)
set(GLFW_INSTALL        OFF CACHE STRING "" FORCE)
add_subdirectory(lib/glfw)
include_directories(lib/glfw/include/GLFW)

#glm
include_directories(lib/glm)

#OpenGL 
find_package( OpenGL REQUIRED )


# ┌──────────────────────────────────────────────────────────────────┐
# │  Build executable                                                │
# └──────────────────────────────────────────────────────────────────┘
add_executable( HelloWorld ./demos/HelloWorld.cpp )
add_executable( SimpleWindow ./demos/SimpleWindow.cpp )

target_link_libraries(SimpleWindow glfw ${OPENGL_gl_LIBRARY})
