cmake_minimum_required (VERSION 3.8)
project (decnum)
add_library (decnum SHARED
  decNumber-icu-368/decContext.c
  decNumber-icu-368/decNumber.c
  decNumber-icu-368/decimal32.c
  decNumber-icu-368/decimal64.c
  decNumber-icu-368/decimal128.c
  decNumber-icu-368/decSingle.c
  decNumber-icu-368/decDouble.c
  decNumber-icu-368/decQuad.c
  decNumber-icu-368/decPacked.c
)
set_property (TARGET decnum APPEND
  PROPERTY COMPILE_FLAGS -fPIC
)
include (GNUInstallDirs)
install (TARGETS decnum DESTINATION ${CMAKE_INSTALL_LIBDIR})
