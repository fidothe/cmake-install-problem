cmake_minimum_required(VERSION 3.27)

project(gubbins)
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_VISIBILITY_PRESET hidden)
set(CMAKE_VISIBILITY_INLINES_HIDDEN YES)

add_library(gubbins SHARED
    src/lib/gubbins.cpp
)
set_target_properties(gubbins PROPERTIES
    SOVERSION 1
    VERSION 1.1.1
)

include(GenerateExportHeader)
generate_export_header(gubbins)
target_sources(gubbins
    PUBLIC
        FILE_SET HEADERS
        BASE_DIRS
            src/include
            ${CMAKE_CURRENT_BINARY_DIR}
)

include(GNUInstallDirs)
install(TARGETS gubbins FILE_SET HEADERS)
