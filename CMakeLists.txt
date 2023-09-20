cmake_minimum_required(VERSION 3.12)

project(MOM6 Fortran)

list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

find_package(fms REQUIRED COMPONENTS R8)

option(SYMMETRIC "Use symmetric memory" ON)
if(SYMMETRIC)
	set(MOM_memory "dynamic_symmetric")
else()
	set(MOM_memory "dynamic_nonsymmetric")
endif()

set(CMAKE_Fortran_FLAGS "${CMAKE_Fortran_FLAGS} -fdefault-real-8 -ffree-line-length-none")

add_subdirectory(MOM6)
add_subdirectory(icebergs)
add_subdirectory(ice_param)
add_subdirectory(SIS2)
add_subdirectory(atmos_null)
add_subdirectory(land_null)

add_subdirectory(coupler)

install(TARGETS MOM6 MOM6-SIS2)
