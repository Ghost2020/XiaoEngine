cmake_minimum_required(VERSION 3.14)
set(CMAKE_CXX_STANDARD 14)

project(XiaoEngine)

find_package(OpenGL REQUIRED)
find_package(GLUT REQUIRED)
# GLFW
# find_package(GLFW REQUIRED)

include_directories(
    $(GLUT_INCLUDE_DIRS)
    # $(GLFW_INCLUDE_DIRS)
)

# link_directories(

# )

add_executable(XiaoEngine main.cpp)

if(MSVC)
    list(APPEND EXTRA_LIBS
        "glu32;opengl32"
    )
elseif(UNIX)
    list(APPEND EXTRA_LIBS
        "-lglu32 -lopengl32"
    )
elseif(APPLE)
    list(APPEND EXTRA_LIBS
        "-framework OpenGL"
    )
endif()

target_link_libraries(XiaoEngine ${EXTRA_LIBS})