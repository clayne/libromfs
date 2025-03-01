cmake_minimum_required(VERSION 3.16)

option(LIBROMFS_PROJECT_NAME "Project name" "")
option(LIBROMFS_RESOURCE_LOCATION "Resource location" "")
option(LIBROMFS_COMPRESS_RESOURCES "If resources should be zlib compressed" ON)

if (NOT LIBROMFS_PROJECT_NAME)
    message(FATAL_ERROR "LIBROMFS_PROJECT_NAME is not set")
endif ()

if (NOT LIBROMFS_RESOURCE_LOCATION)
    message(FATAL_ERROR "LIBROMFS_RESOURCE_LOCATION is not set")
endif ()

project(libromfs_base-${LIBROMFS_PROJECT_NAME})

# Make sure libromfs is configured correctly
if (NOT DEFINED LIBROMFS_RESOURCE_LOCATION)
    message(FATAL_ERROR "To use libromfs, please point the variable LIBROMFS_RESOURCE_LOCATION to a valid folder path")
endif ()

set(LIBROMFS_LIBRARY libromfs-${LIBROMFS_PROJECT_NAME} PARENT_SCOPE)

# Add libromfs components
add_subdirectory(generator)
add_subdirectory(lib)

