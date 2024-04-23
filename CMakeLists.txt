cmake_minimum_required(VERSION 3.21)

# TODO: check android platform

if(CMAKE_TOOLCHAIN_FILE MATCHES "vcpkg.cmake")
if(ANDROID_ABI MATCHES "arm64-v8a")
  set(VCPKG_TARGET_TRIPLET "arm64-android")
elseif(ANDROID_ABI MATCHES "armeabi-v7a")
  set(VCPKG_TARGET_TRIPLET "arm-neon-android")
elseif(ANDROID_ABI MATCHES "x86_64")
  set(VCPKG_TARGET_TRIPLET "x64-android")
elseif(ANDROID_ABI MATCHES "x86")
  set(VCPKG_TARGET_TRIPLET "x86-android")
endif()
endif()

project(
  apc
  VERSION 0.0.1
  DESCRIPTION "Android Performance Counter"
  LANGUAGES CXX
)

# set compile options.
set(CMAKE_CXX_STANDARD 20)

add_subdirectory(apc)

install(EXPORT ${PROJECT_NAME}-config
  NAMESPACE apc::
  DESTINATION ${CMAKE_INSTALL_PREFIX}/share/${PROJECT_NAME}
)
