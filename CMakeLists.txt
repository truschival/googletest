cmake_minimum_required(VERSION 2.6.2)

project( googletest-distribution )

enable_testing()

option(BUILD_GTEST "Builds the googletest subproject" OFF)

#Note that googlemock target already builds googletest
option(BUILD_GMOCK "Builds the googlemock subproject" ON)

if(MINGW)
	MESSAGE(STATUS "MinGW does not always have pthread support, disabling")
	SET(gtest_disable_pthreads On CACHE BOOL  "Enable use of pthreads")
endif(MINGW)

if(BUILD_GMOCK)
  add_subdirectory( googlemock )
elseif(BUILD_GTEST)
  add_subdirectory( googletest )
endif()
