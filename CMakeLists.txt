cmake_minimum_required(VERSION 3.0)
project(Lua)

# Folders
# -------------------------------------------------------------------------------------------------
set(LUA_ROOT_DIR "${CMAKE_CURRENT_LIST_DIR}")

# Source files
# -------------------------------------------------------------------------------------------------
set(LUA_SRC_FILES
	src/lapi.h
	src/lcode.h src/lctype.h src/ldebug.h src/ldo.h src/lfunc.h src/lgc.h src/llex.h
	src/lmem.h src/lobject.h src/lopcodes.h src/lparser.h src/lstate.h src/lstring.h src/ltable.h
	src/ltm.h src/lundump.h src/lvm.h src/lzio.h
	src/lauxlib.h
	src/lapi.c
	src/lcode.c src/lctype.c src/ldebug.c src/ldo.c src/ldump.c src/lfunc.c src/lgc.c src/llex.c
	src/lmem.c src/lobject.c src/lopcodes.c src/lparser.c src/lstate.c src/lstring.c src/ltable.c
	src/ltm.c src/lundump.c src/lvm.c src/lzio.c
	src/lauxlib.c src/lbaselib.c src/lbitlib.c src/lcorolib.c src/ldblib.c src/liolib.c
	src/lmathlib.c src/loslib.c src/lstrlib.c src/ltablib.c src/lutf8lib.c src/loadlib.c src/linit.c
	)

# Target to build
# -------------------------------------------------------------------------------------------------
add_library(lua SHARED ${LUA_SRC_FILES})
target_include_directories(lua
       PUBLIC ${LUA_ROOT_DIR}/src)
if(WIN32)
	target_compile_definitions(lua
		PUBLIC LUA_BUILD_AS_DLL)
endif()
set_target_properties(lua PROPERTIES
	OUTPUT_NAME lua
	DEBUG_POSTFIX _d
	RELWITHDEBINFO_POSTFIX _rd
	MINSIZEREL_POSTFIX _rm)
		