cmake_minimum_required( VERSION 3.2 )

project(cmake_wrapper)

include(conanbuildinfo.cmake)
conan_basic_setup()

add_library(webby
	source_subfolder/webby.h
	source_subfolder/webby.c
	source_subfolder/webby_unix.h
	source_subfolder/webby_win32.h
)

install(
	FILES
		source_subfolder/webby.h
	DESTINATION include
)

install(TARGETS webby
	EXPORT webby
	INCLUDES DESTINATION include
	RUNTIME DESTINATION bin
	LIBRARY DESTINATION lib
	ARCHIVE DESTINATION lib
)

install(
	EXPORT webby
	DESTINATION cmake
)
