cmake_minimum_required(VERSION 3.10)
project(MD5Encrypter)

find_package (Python)

include(FeatureSummary)
feature_summary(WHAT ALL)

#include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
#conan_basic_setup()

include(pmm/pmm.cmake)
pmm(DEBUG CONAN)

add_executable(md5 md5.cpp)
target_include_directories(md5 PRIVATE CONAN_PKG::Poco)
target_link_libraries(md5 PRIVATE CONAN_PKG::Poco)
