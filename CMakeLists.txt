project(SDL_ttf)

include_directories(../SDL/include)
if (WIN32)
  include_directories(VisualC/external/include)
  # "install" freetype .dll for vs 
  file(MAKE_DIRECTORY "${CMAKE_BINARY_DIR}/Debug")
  file(MAKE_DIRECTORY "${CMAKE_BINARY_DIR}/Release")
  configure_file("${PROJECT_SOURCE_DIR}/VisualC/external/lib/x64/libfreetype-6.dll" "${CMAKE_BINARY_DIR}/Debug" COPYONLY)
  configure_file("${PROJECT_SOURCE_DIR}/VisualC/external/lib/x64/libfreetype-6.dll" "${CMAKE_BINARY_DIR}/Release" COPYONLY)
  configure_file("${PROJECT_SOURCE_DIR}/VisualC/external/lib/x64/zlib1.dll" "${CMAKE_BINARY_DIR}/Debug" COPYONLY)
  configure_file("${PROJECT_SOURCE_DIR}/VisualC/external/lib/x64/zlib1.dll" "${CMAKE_BINARY_DIR}/Release" COPYONLY)
else()
  add_subdirectory(external/freetype-2.9.1)
endif()

add_library(SDL2_ttf SDL_ttf.h
                     SDL_ttf.c)
