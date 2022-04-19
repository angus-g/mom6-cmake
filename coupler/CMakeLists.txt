set(coupler_src
  full/atm_land_ice_flux_exchange.F90 full/atmos_ocean_dep_fluxes_calc.F90 full/atmos_ocean_fluxes_calc.F90 full/coupler_main.F90 full/flux_exchange.F90 full/ice_ocean_flux_exchange.F90 full/land_ice_flux_exchange.F90
  shared/surface_flux.F90)

list(TRANSFORM coupler_src PREPEND src/)

add_executable(MOM6-SIS2 ${coupler_src})
target_link_libraries(MOM6-SIS2
  MOM6_cpl bergs_cpl iceparam_cpl SIS2_cpl atmos_cpl land_cpl
  FMS::fms_r8 NetCDF::NetCDF_C)

target_compile_options(MOM6-SIS2 PRIVATE -Duse_AM3_physics -D_USE_LEGACY_LAND_)
