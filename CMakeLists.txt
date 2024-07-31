cmake_minimum_required(VERSION 3.28)
project(ImGui)
set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED True)

file(GLOB_RECURSE SRCS
  ${PROJECT_SOURCE_DIR}/**.cpp
  ${PROJECT_SOURCE_DIR}/**.h
)

add_library(${PROJECT_NAME} STATIC ${SRCS})
target_include_directories(${PROJECT_NAME} PUBLIC
  ${PROJECT_SOURCE_DIR}
)
