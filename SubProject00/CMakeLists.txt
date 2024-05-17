message(STATUS "----- version 0.0------")

add_library(sub STATIC sub.h sub.cpp)

set(sub_INC_DIR ${CMAKE_CURRENT_SOURCE_DIR})
set(sub_LIB_DIR ${CMAKE_CURRENT_SOURCE_DIR}/lib)

option(build_shared OFF)

get_directory_property(has_parent ${CMAKE_CURRENT_SOURCE_DIR} PARENT_DIRECTORY)

if(has_parent)
set(sub_INC_DIR ${CMAKE_CURRENT_SOURCE_DIR} PARENT_SCOPE)
set(sub_LIB_DIR ${CMAKE_CURRENT_SOURCE_DIR}/lib PARENT_SCOPE)
endif()

set_target_properties(sub PROPERTIES
    INCLUDE_DIRECTORIES ${sub_INC_DIR}
    ARCHIVE_OUTPUT_DIRECTORY ${sub_LIB_DIR}
    ARCHIVE_OUTPUT_DIRECTORY_DEBUG ${sub_LIB_DIR}
    ARCHIVE_OUTPUT_DIRECTORY_RELEASE ${sub_LIB_DIR}
)

message(STATUS "build shared = ${build_shared}")



