project(pvr.nextpvr)

cmake_minimum_required(VERSION 2.6)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(xbmc REQUIRED)
find_package(xbmcplatform REQUIRED)
find_package(TinyXML REQUIRED)

include_directories(${xbmcplatform_INCLUDE_DIRS}
                    ${TINYXML_INCLUDE_DIR}
                    ${XBMC_INCLUDE_DIR})

set(NEXTPVR_SOURCES src/client.cpp
                    src/DialogRecordPref.cpp
                    src/liveshift.cpp
                    src/md5.cpp
                    src/pvrclient-nextpvr.cpp
                    src/RingBuffer.cpp
                    src/Socket.cpp
                    src/uri.cpp)

SET(DEPLIBS ${xbmcplatform_LIBRARIES}
            ${TINYXML_LIBRARIES})

build_addon(pvr.nextpvr NEXTPVR DEPLIBS)

include(CPack)
