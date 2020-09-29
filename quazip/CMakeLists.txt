file(GLOB SRCS "*.c" "*.cpp")
file(GLOB PUBLIC_HEADERS "*.h")

set(SRCS ${SRCS} ${PUBLIC_HEADERS})
set(INCS ${ZLIB_INCLUDE_DIR})
set(DEFS QUAZIP_BUILD)
set(LIBS Qt5::Core zlib)

__add_real_target(quazip dll SOURCE ${SRCS} DEF ${DEFS} LIB ${LIBS})
