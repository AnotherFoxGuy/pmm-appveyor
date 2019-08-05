cmake_minimum_required(VERSION 3.10)
include(FetchContent)

project(MD5Encrypter)

#include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
#conan_basic_setup()

set(FETCHCONTENT_QUIET OFF)

FetchContent_Declare(
        PMM_REPO
        GIT_REPOSITORY https://github.com/AnotherFoxGuy/pmm.git
	      GIT_TAG vcoutput
)

FetchContent_GetProperties(PMM_REPO)
if (NOT pmm_repo_POPULATED)
    FetchContent_Populate(PMM_REPO)
endif ()

include(${pmm_repo_SOURCE_DIR}/pmm.cmake)
set(PMM_ALWAYS_DOWNLOAD TRUE)
set(PMM_URL "file://${pmm_repo_SOURCE_DIR}/pmm")

pmm(VCPKG REVISION f9fedc930cf36ce6cec69a3d09879b3c7f23eb0b REQUIRES poco)

add_executable(md5 md5.cpp)
target_include_directories(md5 PRIVATE poco::poco)
target_link_libraries(md5 PRIVATE poco::poco)
