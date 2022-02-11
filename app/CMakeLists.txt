add_executable(hello_world hello_world.cc)
target_link_libraries(hello_world PUBLIC ${CMAKE_PROJECT_NAME})