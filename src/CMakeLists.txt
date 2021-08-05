cmake_minimum_required (VERSION 3.8)

# ���ҵ�ǰĿ¼�µ�����Դ�ļ�
aux_source_directory(${CMAKE_CURRENT_SOURCE_DIR} source)
# �������ӿ�
add_library(csofa ${source})

add_library(csofa::csofa ALIAS csofa) 

set_target_properties(csofa
                      PROPERTIES
                      VERSION ${${PROJECT_NAME}_VERSION}
                      SOVERSION ${${PROJECT_NAME}_VERSION_MAJOR})

set(TARGETS_EXPORT_NAME "${PROJECT_NAME}Targets") 

install(TARGETS csofa
        EXPORT ${TARGETS_EXPORT_NAME}
        RUNTIME DESTINATION bin
        LIBRARY DESTINATION lib
        ARCHIVE DESTINATION lib
        PUBLIC_HEADER DESTINATION include
)

include(CMakePackageConfigHelpers)
configure_package_config_file(
    "${PROJECT_SOURCE_DIR}/cmake/${PROJECT_NAME}Config.cmake"
    "${PROJECT_BINARY_DIR}/${PROJECT_NAME}Config.cmake"
    INSTALL_DESTINATION lib/cmake/${PROJECT_NAME}
)

install(FILES "${PROJECT_BINARY_DIR}/${PROJECT_NAME}Config.cmake"
        DESTINATION lib/cmake/${PROJECT_NAME})

install(
  EXPORT ${TARGETS_EXPORT_NAME} 
  DESTINATION "${CMAKE_INSTALL_LIBDIR}/cmake/${PROJECT_NAME}"
)