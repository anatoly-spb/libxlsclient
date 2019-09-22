project(xls)

# создать проект из шаблона
configure_file(
	external/CMakeLists.txt.in 
	${CMAKE_CURRENT_BINARY_DIR}/external/CMakeLists.txt
)
# сконфигурировать
execute_process(
	COMMAND ${CMAKE_COMMAND} -G "${CMAKE_GENERATOR}" .
  	WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/external
)
# собрать
execute_process(
	COMMAND ${CMAKE_COMMAND} --build .
  	WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/external
)
include(${CMAKE_CURRENT_BINARY_DIR}/external/xls-prefix/cmake/xls-targets.cmake)
if(TARGET xls) 
  message("XLS EXISTS")
endif()
