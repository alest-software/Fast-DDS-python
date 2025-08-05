cmake_minimum_required(VERSION 3.15)
project(fastddspython_ex VERSION 2.3.0)

set(CMAKE_PREFIX_PATH "/opt/fastdds")
set(CMAKE_INSTALL_PREFIX "/opt/fastdds")

add_subdirectory(Fast-DDS-python/fastdds_python)

include(InstallRequiredSystemLibraries)

if(NOT DEFINED CPACK_PACKAGE_VERSION)
    set(CPACK_PACKAGE_VERSION ${PROJECT_VERSION})
endif()

if(DEFINED CPACK_DEBIAN_PACKAGE_REVISION)
    set(CPACK_PACKAGE_VERSION "${CPACK_PACKAGE_VERSION}-${CPACK_DEBIAN_PACKAGE_REVISION}")
endif()

set(CPACK_PACKAGE_NAME "libfastdds-python")
set(CPACK_PACKAGE_CONTACT "you@example.com")
set(CPACK_DEBIAN_PACKAGE_DEPENDS "libc6")
set(CPACK_GENERATOR "DEB")

set(CPACK_PACKAGE_FILE_NAME "${CPACK_PACKAGE_NAME}_${CPACK_PACKAGE_VERSION}_${CPACK_DEBIAN_PACKAGE_ARCHITECTURE}")

include(CPack)

