add_library(pex_exceptions SHARED)

target_compile_features(pex_exceptions PUBLIC cxx_std_14)
set_target_properties(pex_exceptions PROPERTIES 
    CXX_EXTENSIONS OFF
    POSITION_INDEPENDENT_CODE ON
)

target_include_directories(pex_exceptions PUBLIC
    ${PROJECT_SOURCE_DIR}/include
)

target_sources(pex_exceptions PRIVATE
    Exception.cc
)

target_link_libraries(pex_exceptions PUBLIC
    base
)

install(TARGETS pex_exceptions)
