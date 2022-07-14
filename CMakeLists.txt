# CMakeList.txt: csofa 的 CMake 项目，在此处包括源代码并定义
# 项目特定的逻辑。
#
cmake_minimum_required (VERSION 3.15)

project (csofa VERSION 1.0 LANGUAGES C)

# 设置C++版本
# set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS ON)
# set(CMAKE_CXX_STANDARD 20)
# set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_compile_options("$<$<C_COMPILER_ID:MSVC>:/utf-8>")
add_compile_options("$<$<CXX_COMPILER_ID:MSVC>:/utf-8>")

#最后引用子文件夹里的CMakeLists.txt，提供一个选项是否编译Test
option(BUILD_csofa_TESTS "Build Tests" ON)

include(GNUInstallDirs)

# include(GenerateExportHeader)
if(MSVC)
    set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS TRUE)
    set(BUILD_SHARED_LIBS TRUE)
endif()

add_subdirectory(src)

add_subdirectory(include)

if(BUILD_csofa_TESTS)    
	enable_testing()    
	add_subdirectory(test)
endif()

