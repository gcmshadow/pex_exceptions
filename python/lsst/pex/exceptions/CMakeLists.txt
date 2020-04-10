find_package(pybind11 REQUIRED)

pybind11_add_module(exceptions exceptions.cc)
target_link_libraries(exceptions PUBLIC pex_exceptions)
install(TARGETS exceptions DESTINATION ${CMAKE_INSTALL_PREFIX}/python/lsst/pex/exceptions)

file(GENERATE OUTPUT ${CMAKE_CURRENT_BINARY_DIR}/version.py CONTENT "\
__version__ = 'unknown'
__all__ = ('__version__',)
")

install(FILES ${CMAKE_CURRENT_BINARY_DIR}/version.py DESTINATION ${CMAKE_INSTALL_PREFIX}/python/lsst/pex/exceptions)

install(
    DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/ DESTINATION ${CMAKE_INSTALL_PREFIX}/python/lsst/pex/exceptions
    PATTERN "CMakeLists.txt" EXCLUDE
    PATTERN "SConscript" EXCLUDE
    PATTERN "*.cc" EXCLUDE
)
