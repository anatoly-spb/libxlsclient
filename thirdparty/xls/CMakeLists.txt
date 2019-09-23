project(xls)

include(ExternalProject)
ExternalProject_Add(external-xls
  GIT_REPOSITORY https://github.com/anatoly-spb/libxls.git
  GIT_TAG master
  CMAKE_ARGS
	-DCMAKE_INSTALL_PREFIX:PATH=<INSTALL_DIR>
	-debug-output
  UPDATE_COMMAND ""
  TEST_BEFORE_INSTALL ON
  LOG_DOWNLOAD ON
  LOG_CONFIGURE ON
  LOG_BUILD ON
  LOG_TEST ON
  LOG_INSTALL ON
)
ExternalProject_Get_Property(external-xls INSTALL_DIR)
add_library(xls STATIC IMPORTED GLOBAL)
add_dependencies(xls external-xls)
file(MAKE_DIRECTORY ${INSTALL_DIR}/lib)
file(MAKE_DIRECTORY ${INSTALL_DIR}/include)
set_target_properties(xls PROPERTIES
  IMPORTED_LOCATION ${INSTALL_DIR}/lib/${CMAKE_STATIC_LIBRARY_PREFIX}xls${CMAKE_STATIC_LIBRARY_SUFFIX}
  INTERFACE_INCLUDE_DIRECTORIES ${INSTALL_DIR}/include
)

