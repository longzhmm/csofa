cmake_minimum_required (VERSION 3.15)

# 查找当前目录下的所有源文件
aux_source_directory(${CMAKE_CURRENT_SOURCE_DIR} source)
# 生成链接库
add_library(csofa ${source})

#GENERATE_EXPORT_HEADER(csofa
#                       BASE_NAME csofa
#                       EXPORT_MACRO_NAME csofa_EXPORTS
#                       EXPORT_FILE_NAME csofa_exports.h
#                       STATIC_DEFINE SHARED_EXPORTS_BUILT_AS_STATIC)

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
