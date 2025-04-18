# ==============================================================================
# AMS - Advanced Module System
# ==============================================================================

CMAKE_MINIMUM_REQUIRED(VERSION 3.10 FATAL_ERROR)
#SET(CMAKE_VERBOSE_MAKEFILE ON)
PROJECT(AMSBUILD)

# ==============================================================================
# project setup ----------------------------------------------------------------
# ==============================================================================

# what languages we use ---------------------------
ENABLE_LANGUAGE(C)
ENABLE_LANGUAGE(CXX)

# this is composite project ----------------------
SET(COMPOSITE_PROJECT TRUE)
SET(DEVELOPMENT_ROOT "${CMAKE_BINARY_DIR}/src")

# extra options ----------------------------------
SET(TRY_QT_LIB          OFF  CACHE INTERNAL "QT is not neccessary" FORCE)

# ==============================================================================
# libraries --------------------------------------------------------------------
# ==============================================================================

LINK_DIRECTORIES(${CMAKE_BINARY_DIR}/lib)

# ==============================================================================
# rpaths -----------------------------------------------------------------------
# ==============================================================================

# use, i.e. don't skip the full RPATH for the build tree
SET(CMAKE_SKIP_BUILD_RPATH  FALSE)

# when building, don't use the install RPATH already
# (but later on when installing)
SET(CMAKE_BUILD_WITH_INSTALL_RPATH FALSE) 

# the RPATH to be used when installing
SET(CMAKE_INSTALL_RPATH "${CMAKE_INSTALL_PREFIX}/lib")

# add the automatically determined parts of the RPATH
# which point to directories outside the build tree to the install RPATH
SET(CMAKE_INSTALL_RPATH_USE_LINK_PATH FALSE)

# ==============================================================================
# compiler setups --------------------------------------------------------------
# ==============================================================================

# C options
SET(CMAKE_C_FLAGS_RELEASE "-O2 -m64")
SET(CMAKE_C_FLAGS_DEBUG "-g -m64 -Wall -Werror -pedantic-errors -Wundef -Wno-long-long")

# C++ options
SET(CMAKE_CXX_FLAGS_RELEASE "-O2 -std=c++11 -m64")
SET(CMAKE_CXX_FLAGS_DEBUG "-O0 -std=c++11 -m64 -g -Wall -Werror -pedantic-errors -Wundef -Wno-long-long")

SET(CMAKE_BUILD_TYPE Release)
#SET(CMAKE_BUILD_TYPE Debug)

# ==============================================================================
# project subdirectories  ------------------------------------------------------
# ==============================================================================

ADD_SUBDIRECTORY(src/thirdparty/hwloc/2.11.2)
# projects ---------------------------------------
ADD_SUBDIRECTORY(src/projects/hipoly/1.0)
ADD_SUBDIRECTORY(src/projects/ams/9.0)

# ==============================================================================
# inter-project dependencies  --------------------------------------------------
# ==============================================================================

ADD_DEPENDENCIES(ams_shared hipoly_shared hwloc-build)

