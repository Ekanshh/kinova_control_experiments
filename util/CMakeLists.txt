add_library(kinova_util STATIC
    ${CMAKE_CURRENT_LIST_DIR}/kinova_util.cpp
    ${CMAKE_CURRENT_LIST_DIR}/util.cpp
)
target_include_directories(kinova_util PUBLIC ${CMAKE_CURRENT_LIST_DIR})
target_link_libraries(kinova_util PUBLIC abag kinova_api)