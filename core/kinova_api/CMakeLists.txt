set(KINOVA_API_VERSION v1.1.6.0)
set(kinova_api_INCLUDE_DIR ${CMAKE_CURRENT_LIST_DIR}/linux_gcc_x86-64/include)
set(kinova_api_LIB_DIR ${CMAKE_CURRENT_LIST_DIR}/linux_gcc_x86-64/lib/release)

# Function to recursively find and add include directories
function(add_include_subdirectories base_dir)
    file(GLOB_RECURSE header_files "${base_dir}/*.h")

    set(include_dirs ${base_dir})

    foreach(header ${header_files})
        get_filename_component(dir ${header} DIRECTORY)
        list(APPEND include_dirs ${dir})
    endforeach()

    list(REMOVE_DUPLICATES include_dirs)
    set(kinova_api_INCLUDE_DIRS ${include_dirs} PARENT_SCOPE)
endfunction()

# Add all subdirectories in the include directory to the include path
add_include_subdirectories(${kinova_api_INCLUDE_DIR})

# Create an INTERFACE library for Kinova API
add_library(kinova_api INTERFACE)
target_include_directories(kinova_api INTERFACE ${kinova_api_INCLUDE_DIRS})
target_link_libraries(kinova_api INTERFACE ${kinova_api_LIB_DIR}/libKortexApiCpp.a)

# Optionally, print the include directories for debugging
message(STATUS "Kinova Kortex CPP API include directories:")

foreach(dir ${kinova_api_INCLUDE_DIRS})
    message(STATUS "  ${dir}")
endforeach()