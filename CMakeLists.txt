cmake_minimum_required(VERSION 3.30)

project("qu3e")

set(qu3e_version 1.1)

option(qu3e_build_shared "Build qu3e shared libraries" OFF)
option(qu3e_build_static "Build qu3e static libraries" ON)
option(qu3e_build_demo "Build qu3e demo" ON)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

add_subdirectory(src)

add_compile_definitions(GL_SILENCE_DEPRECATION)

if(qu3e_build_demo)
	find_package(OpenGL REQUIRED)
	add_subdirectory(freeglut)
	add_subdirectory(demo)
	add_subdirectory(imgui)
endif()
