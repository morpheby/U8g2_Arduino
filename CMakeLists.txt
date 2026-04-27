if(ESP_PLATFORM)
    idf_component_register(SRC_DIRS "src" "src/clib"
                        INCLUDE_DIRS "src" "src/clib"
                        REQUIRES "arduino")
    return()
endif()

cmake_minimum_required(VERSION 3.16)

if(CMAKE_CURRENT_SOURCE_DIR STREQUAL CMAKE_SOURCE_DIR)
    project(U8g2_Arduino CXX C)
endif()

file(GLOB _U8G2_CLIB "${CMAKE_CURRENT_SOURCE_DIR}/src/clib/*.c")
add_library(U8g2_Arduino STATIC
    ${_U8G2_CLIB}
    "${CMAKE_CURRENT_SOURCE_DIR}/src/U8x8lib.cpp"
    "${CMAKE_CURRENT_SOURCE_DIR}/src/U8g2lib.cpp"
)
target_include_directories(U8g2_Arduino PUBLIC
    "${CMAKE_CURRENT_SOURCE_DIR}/src"
    "${CMAKE_CURRENT_SOURCE_DIR}/src/clib"
)
