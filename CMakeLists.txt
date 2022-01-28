cmake_minimum_required(VERSION 3.19)

set(NUGET_COMMAND "" CACHE STRING "NuGet executable used for package installs.")
if(DEFINED WIN32 AND "${NUGET_COMMAND}" STREQUAL "")
  set(NUGET_COMMAND ${CMAKE_CURRENT_SOURCE_DIR}/nuget.exe)
  if(NOT EXISTS ${NUGET_COMMAND})
    file(DOWNLOAD https://dist.nuget.org/win-x86-commandline/latest/nuget.exe ${NUGET_COMMAND})
    message(STATUS "NUGET_COMMAND = ${NUGET_COMMAND}")
  endif()
endif()

project(test-boost-cmake)
