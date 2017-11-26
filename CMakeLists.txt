cmake_minimum_required(VERSION 3.1)
project(OpenSWE1R)

set(CMAKE_C_STANDARD 11)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake/")

find_package(Unicorn REQUIRED)
find_package(OpenGL REQUIRED)
find_package(GLEW REQUIRED)
find_package(SDL2 REQUIRED)
find_package(DevIL REQUIRED)

include_directories(SYSTEM
	${LIBUNICORN_INCLUDE_DIR}
	${OPENGL_INCLUDE_DIR}
	${GLEW_INCLUDE_DIRS}
  ${SDL2_INCLUDE_DIR}
  ${IL_INCLUDE_DIR}
)

add_executable(openswe1r
  main.c
  emulation.c
  export.c
  shader.c

  dll/kernel32.c

  com/dplay.c
)

target_link_libraries(openswe1r
	${LIBUNICORN_LIBRARY}
	${OPENGL_LIBRARIES}
	${GLEW_LIBRARIES}
  ${SDL2_LIBRARY}
  ${IL_LIBRARIES}
  ${ILU_LIBRARIES}
)