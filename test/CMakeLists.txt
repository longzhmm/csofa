cmake_minimum_required(VERSION 3.15) 

macro(add_csofa_test _TEST_NAME)
    set(test_name test_${_TEST_NAME})
    add_executable(test_${_TEST_NAME} t_sofa_c.c)
    target_link_libraries(test_${_TEST_NAME} PRIVATE csofa::csofa)
    add_test(NAME csofa_test_${_TEST_NAME} COMMAND test_${_TEST_NAME})
    # Group under the "tests" project folder in IDEs such as Visual Studio.
    set_property(TARGET test_${_TEST_NAME} PROPERTY FOLDER "Tests")
#    if(WIN32 AND BUILD_SHARED_LIBS)
#        add_custom_command(TARGET test_${_TEST_NAME} POST_BUILD 
#                           COMMAND ${CMAKE_COMMAND} -E copy $<TARGET_FILE:csofa> $<TARGET_FILE_DIR:test_${_TEST_NAME}>)
#    endif()
endmacro()

add_csofa_test(csofa)

# add_custom_command(TARGET ${test_name}
#                   POST_BUILD 
#                   COMMAND ${CMAKE_COMMAND} -E make_directory $<TARGET_FILE_DIR:test_file>/data)

# add_custom_command(TARGET ${test_name}
#                   POST_BUILD 
#                   COMMAND ${CMAKE_COMMAND} -E copy ${CMAKE_CURRENT_SOURCE_DIR}/data/test_data.dat
#                   $<TARGET_FILE_DIR:test_file>/data/test_data.dat)