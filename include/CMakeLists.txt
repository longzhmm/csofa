cmake_minimum_required (VERSION 3.15)

target_include_directories(csofa PUBLIC  
    $<INSTALL_INTERFACE:include>    
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>)

target_sources(csofa PRIVATE
     # Header files (useful in IDEs)
    "csofa/sofa.h"
    "csofa/sofam.h"
)
install(DIRECTORY csofa DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})