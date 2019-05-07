cmake_minimum_required(VERSION 3.10)
include(FetchContent)

project(MD5Encrypter)

#include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
#conan_basic_setup()

set(FETCHCONTENT_QUIET OFF)

FetchContent_Declare(
        PMM_REPO
        GIT_REPOSITORY https://github.com/vector-of-bool/pmm.git
	      GIT_TAG develop
)

FetchContent_GetProperties(PMM_REPO)
if (NOT pmm_repo_POPULATED)
    FetchContent_Populate(PMM_REPO)
endif ()

include(${pmm_repo_SOURCE_DIR}/pmm.cmake)
pmm(DEBUG CONAN BINCRAFTERS)

add_executable(md5 md5.cpp)
target_include_directories(md5 PRIVATE CONAN_PKG::Poco)
target_link_libraries(md5 PRIVATE CONAN_PKG::Poco)
