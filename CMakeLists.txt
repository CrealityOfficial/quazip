__files_group(${CMAKE_CURRENT_SOURCE_DIR}/quazip/ SRCS)

set(DEFS QUAZIP_STATIC)

__cc_find(zlib_static)

if(NOT TARGET Qt5::Core)
	__prepare_core_qt5()
endif()

set(LIBS Qt5::Core zlib_static)

__add_real_target(quazip_static lib SOURCE ${SRCS}
						 DEF ${DEFS}
						 INTERFACE_DEF QUAZIP_STATIC
						 INC ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/quazip/
						 ILIB ${LIBS}
						 INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}
						 )

if(CC_INSTALL_QUAZIP_STATIC)
	__install_directory_specif(${CMAKE_CURRENT_SOURCE_DIR}/quazip quazip_static)
endif()
