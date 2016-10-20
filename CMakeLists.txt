cmake_minimum_required(VERSION 3.3)
set(LFL_OSX_CERT OSX Developer \(FFFFFFFFFF\))
set(LFL_IOS_CERT iPhone Developer \(FFFFFFFFFF\))
set(LFL_IOS_PROVISION /Users/developer/Downloads/developer.mobileprovision)

# os
include(core/CMake/LFLOS.cmake)

set(LFL_FLATBUFFERS 1)
set(LFL_PNG 1)
set(LFL_GIF 1)
set(LFL_JPEG 1)
set(LFL_BOX2D 1)
set(LFL_SQLITE 1)
set(LFL_SQLCIPHER 1)
set(LFL_PROTOBUF 1)
set(LFL_CRITTERCISM 1)
set(LFL_HOCKEYAPP 1)
set(LFL_REF10EXTRACT 1)
set(LFL_MOSH 1)

# configure
if(LFL_IOS)
  set(LFL_AUDIOUNIT 1)
  set(LFL_OPENCV 1)
  set(LFL_OPENSSL 1)
elseif(LFL_ANDROID)
  set(LFL_OPENCV 1)
  set(LFL_FREETYPE 1)
  set(LFL_OPENSSL 1)
  set(LFL_GTEST 1)
elseif(LFL_EMSCRIPTEN)
  set(LFL_SDL 1)
  set(LFL_OPENAL 1)
else()
  if(NOT WIN32)
    set(LFL_GLOG 1)
    set(LFL_QT 1)
    set(LFL_FREETYPE 1)
  endif()
  set(LFL_OPENSSL 1)
  set(LFL_GTEST 1)
  set(LFL_LIBARCHIVE 1)
  set(LFL_RE2 1)
  #set(LFL_GEOIP 1)
  set(LFL_PCAP 1)
  set(LFL_LIBCLANG 1)
  set(LFL_LIBCLING 1)
  set(LFL_JSONCPP 1)
  set(LFL_LIBCSS 1)
  set(LFL_V8JS 1)
  set(LFL_GLEW 1)
  #set(LFL_WXWIDGETS 1)
  #set(LFL_HARFBUZZ 1)
  set(LFL_OPENCV 1)
  set(LFL_FFMPEG 1)
  set(LFL_X264 1)
  set(LFL_LAME 1)
  set(LFL_OPENAL 1)
  #set(LFL_BERKELIUM 1)
  #set(LFL_PORTAUDIO 1)
  #set(LFL_GLFW 1)
  #set(LFL_SDL 1)
  #set(LFL_CUDA 1)
  set(LFL_LIBUV 1)
  set(LFL_CMAKEDAEMON 1)
endif()

if(NOT WIN32 AND NOT LFL_ANDROID)
  set(LFL_ICONV 1)
endif()

# external imports
set(V8_DIR $ENV{HOME}/v8)
set(LLVM_DIR $ENV{HOME}/llvm)
set(CLING_LLVM_DIR $ENV{HOME}/cling-build/inst)

# core
set(LFL_SOURCE_DIR ${CMAKE_CURRENT_SOURCE_DIR})
set(LFL_BINARY_DIR ${CMAKE_CURRENT_BINARY_DIR})
set(LFL_CORE_BINARY_DIR ${CMAKE_CURRENT_BINARY_DIR}/core)
set(LFL_OS_CORE_BINARY_DIR ${CMAKE_CURRENT_BINARY_DIR}/../${LFL_OS}/core)
include(core/CMake/LFLCore.cmake)

# crystal bawl
add_subdirectory(cb)

# data miner
add_subdirectory(miner)

# fusion sensor
add_subdirectory(fs)

# calculator
add_subdirectory(calculator)

# terminal
add_subdirectory(term)

# editor
add_subdirectory(editor)

# web browser
add_subdirectory(browser)

# chess
add_subdirectory(chess)

# spaceball
add_subdirectory(spaceball)

# image util
add_subdirectory(image)

# master server list
add_subdirectory(master)

# email marketing
add_subdirectory(blaster)

# market app
add_subdirectory(market)

# q3 clone
add_subdirectory(quake)

# irc bots
add_subdirectory(senators)
