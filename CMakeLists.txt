cmake_minimum_required(VERSION 3.28)
project(ImGui)
set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED True)

set(BUILD_SHARED_LIBS OFF)

file(GLOB_RECURSE SRCS
  ${PROJECT_SOURCE_DIR}/**.cpp
  ${PROJECT_SOURCE_DIR}/**.h
)

FetchContent_Declare(freetype
        GIT_REPOSITORY https://github.com/freetype/freetype.git
)
FetchContent_MakeAvailable(freetype)
FetchContent_GetProperties(freetype SOURCE_DIR freetype_SOURCE_DIR)

FetchContent_Declare(lunasvg
        GIT_REPOSITORY https://github.com/sammycage/lunasvg.git
        GIT_TAG 73da3ef408b934e0fe001c7b163df2e28d4713e7
)
FetchContent_MakeAvailable(lunasvg)
FetchContent_GetProperties(lunasvg SOURCE_DIR lunasvg_SOURCE_DIR)

add_library(${PROJECT_NAME} STATIC ${SRCS})
target_link_libraries(${PROJECT_NAME} PUBLIC freetype lunasvg)
target_include_directories(${PROJECT_NAME} PUBLIC
  ${PROJECT_SOURCE_DIR}
  ${lunasvg_SOURCE_DIR}/include
  ${freetype_SOURCE_DIR}/include
)
