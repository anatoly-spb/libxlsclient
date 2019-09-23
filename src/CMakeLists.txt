project(xlstest)
find_file(XLS_TEST_FILE NAMES test.xls PATHS ${CMAKE_CURRENT_SOURCE_DIR} NO_DEFAULT_PATH)
configure_file(
	test.h.in 
	${CMAKE_CURRENT_BINARY_DIR}/test.h
	@ONLY
)
add_executable(xlstest test.c)
target_link_libraries(xlstest xls)
target_include_directories(xlstest PRIVATE ${CMAKE_CURRENT_BINARY_DIR})
