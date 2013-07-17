PROJECT(pvr.nextpvr)

CMAKE_MINIMUM_REQUIRED(VERSION 2.6)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${PROJECT_SOURCE_DIR})

ENABLE_LANGUAGE(CXX)

FIND_PACKAGE(xbmc REQUIRED)
FIND_PACKAGE(xbmcplatform REQUIRED)
FIND_PACKAGE(TinyXML REQUIRED)

addon_version(pvr.nextpvr NEXTPVR)

INCLUDE_DIRECTORIES(${xbmcplatform_INCLUDE_DIRS}
                    ${TINYXML_INCLUDE_DIR}
                    ${XBMC_INCLUDE_DIR})

SET(SOURCES src/client.cpp
            src/liveshift.cpp
            src/md5.cpp
            src/pvrclient-nextpvr.cpp
            src/RingBuffer.cpp
            src/Socket.cpp
            src/uri.cpp)

SET(DEPLIBS ${xbmcplatform_LIBRARIES}
            ${TINYXML_LIBRARIES})

build_addon(pvr.nextpvr SOURCES DEPLIBS NEXTPVR_VERSION)
install_addon(pvr.nextpvr ${NEXTPVR_VERSION})
