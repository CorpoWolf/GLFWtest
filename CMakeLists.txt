cmake_minimum_required(VERSION 3.8)
project(MyProject)

# specify the C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# include directories
include_directories("H:/Coding/01_Libs/GLFW/include")
include_directories("H:/Coding/01_Libs/glad/include")
# include_directories("C:/Program Files (x86)/Windows Kits/10/Include/10.0.22000.0/um")
# include_directories("C:/Program Files (x86)/Windows Kits/10/Include/10.0.22000.0/shared")

# find libraries
find_library(GLFW_LIB glfw3 PATHS "H:/Coding/01_Libs/GLFW/lib-vc2022" NO_DEFAULT_PATH)
find_library(OPENGL_LIB OpenGL32 PATHS "C:/Program Files (x86)/Windows Kits/10/Lib/10.0.22000.0/um/x64" NO_DEFAULT_PATH)

# specify the target architecture
set(CMAKE_GENERATOR_PLATFORM x64)

# specify the source files
set(SOURCES
    src/main.cpp
    "H:/Coding/01_Libs/glad/src/glad.c"
)

# specify the executable
add_executable(MyProject ${SOURCES})

# link GLFW library
target_link_libraries(MyProject ${GLFW_LIB})

# link OpenGL library
target_link_libraries(MyProject "-lOpenGL32")
