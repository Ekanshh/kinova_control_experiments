# Set abag.c to compile as C
set_source_files_properties(${CMAKE_CURRENT_LIST_DIR}/abag.c PROPERTIES LANGUAGE C)

# Create a static library from abag.c (compiled as C)
add_library(abag STATIC ${CMAKE_CURRENT_LIST_DIR}/abag.c)

# Include the directory for header files
target_include_directories(abag PUBLIC ${CMAKE_CURRENT_LIST_DIR})

# print the include directories for debugging
message(STATUS "ABAG include directories:")
foreach(dir ${CMAKE_CURRENT_LIST_DIR})
    message(STATUS "  ${dir}")
endforeach()