# types library
csptypesimpl_public_headers = [
    'CspTypeFactory.h',
    'PyCspEnum.h',
    'PyCspType.h',
    'PyStruct.h',
    'PyStructList.h',
    'PyStructList_impl.h',
    'PyStructFastList.h',
    'PyStructFastList_impl.h',
    'VectorWrapper.h',
]
csptypesimpl = py.extension_module(
    '_csptypesimpl',
    'csptypesimpl.cpp',
    'CspTypeFactory.cpp',
    'PyCspEnum.cpp',
    'PyCspType.cpp',
    'PyStruct.cpp',
    'PyStructToJson.cpp',
    'PyStructToDict.cpp',
    cpp_args: ['-DRAPIDJSON_HAS_STDSTRING=1', '-DCSPTYPESIMPL_EXPORTS=1'],
    dependencies: [csp_core, csp_types],
    install: true,
    subdir: 'csp/lib',
    install_tag: 'python-runtime',
)
# set_target_properties(['csptypesimpl', 'PROPERTIES', 'PUBLIC_HEADER', '${CSPTYPESIMPL_PUBLIC_HEADERS}'])
# target_compile_definitions(['csptypesimpl', 'PUBLIC', 'RAPIDJSON_HAS_STDSTRING=1'])
# target_link_libraries(['csptypesimpl', 'csp_core', 'csp_types'])
# target_compile_definitions(['csptypesimpl', 'PRIVATE', 'CSPTYPESIMPL_EXPORTS=1'])
cspimpl_public_headers = [
    'Common.h',
    'Conversions.h',
    'Exception.h',
    'InitHelper.h',
    'NumpyConversions.h',
    'NumpyInputAdapter.h',
    'PyAdapterManagerWrapper.h',
    'PyBasketInputProxy.h',
    'PyBasketOutputProxy.h',
    'PyCppNode.h',
    'PyEngine.h',
    'PyInputAdapterWrapper.h',
    'PyInputProxy.h',
    'PyIterator.h',
    'PyCppNode.h',
    'PyNode.h',
    'PyNodeWrapper.h',
    'PyNumbaNode.h',
    'PyObjectPtr.h',
    'PyOutputAdapterWrapper.h',
    'PyOutputProxy.h',
    'PyConstants.h',
    'PyStructToJson.h',
    'PyStructToDict.h',
]
cspimpl = py.extension_module(
    '_cspimpl',
    'cspimpl.cpp',
    'Conversions.cpp',
    'NumpyConversions.cpp',
    'PyAdapterManager.cpp',
    'PyAdapterManagerWrapper.cpp',
    'PyConstAdapter.cpp',
    'PyCppNode.cpp',
    'PyEngine.cpp',
    'PyGraphOutputAdapter.cpp',
    'PyInputAdapterWrapper.cpp',
    'PyBasketInputProxy.cpp',
    'PyBasketOutputProxy.cpp',
    'PyDynamicNode.cpp',
    'PyFeedbackAdapter.cpp',
    'PyInputProxy.cpp',
    'PyNode.cpp',
    'PyNodeWrapper.cpp',
    'PyNumbaNode.cpp',
    'PyNumpyAdapter.cpp',
    'PyOutputAdapter.cpp',
    'PyOutputAdapterWrapper.cpp',
    'PyOutputProxy.cpp',
    'PyPullInputAdapter.cpp',
    'PyPushInputAdapter.cpp',
    'PyPushPullInputAdapter.cpp',
    'PyManagedSimInputAdapter.cpp',
    'PyTimerAdapter.cpp',
    'PyConstants.cpp',
    # cspimpl_public_headers,
    cpp_args: ['-DNPY_NO_DEPRECATED_API=NPY_1_7_API_VERSION', '-DCSPIMPL_EXPORTS=1'],
    dependencies: [csp_core, csp_engine],
    link_with: csptypesimpl,
    install: true,
    subdir: 'csp/lib',
    install_tag: 'python-runtime',
)

# set_target_properties(['cspimpl', 'PROPERTIES', 'PUBLIC_HEADER', '${CSPIMPL_PUBLIC_HEADERS}'])
# target_link_libraries(['cspimpl', 'csptypesimpl', 'csp_core', 'csp_engine'])
# target_compile_definitions(['cspimpl', 'PUBLIC', 'NPY_NO_DEPRECATED_API=NPY_1_7_API_VERSION'])
# target_compile_definitions(['cspimpl', 'PRIVATE', 'CSPIMPL_EXPORTS=1'])
## Baselib c++ module
cspbaselibimpl = py.extension_module(
    '_cspbaselibimpl',
    'cspbaselibimpl.cpp',
    dependencies: baselibimpl,
    link_with: cspimpl,
    install: true,
    subdir: 'csp/lib',
    install_tag: 'python-runtime',
)
# target_link_libraries(['cspbaselibimpl', 'cspimpl', 'baselibimpl'])
# Include exprtk include directory for exprtk node
# target_include_directories(['cspbaselibimpl', 'PRIVATE', exprtk_include_dirs])
## Basketlib c++ module
cspbasketlibimpl = py.extension_module(
    '_cspbasketlibimpl',
    'cspbasketlibimpl.cpp',
    dependencies: basketlibimpl,
    link_with: cspimpl,
    install: true,
    subdir: 'csp/lib',
    install_tag: 'python-runtime',
)
# target_link_libraries(['cspbasketlibimpl', 'cspimpl', 'basketlibimpl'])
## Math c++ module
cspmathimpl = py.extension_module(
    '_cspmathimpl',
    'cspmathimpl.cpp',
    dependencies: mathimpl,
    link_with: cspimpl,
    install: true,
    subdir: 'csp/lib',
    install_tag: 'python-runtime',
)
# target_link_libraries(['cspmathimpl', 'cspimpl', 'mathimpl'])
## Stats c++ module
cspstatsimpl = py.extension_module(
    '_cspstatsimpl',
    'cspstatsimpl.cpp',
    dependencies: statsimpl,
    link_with: cspimpl,
    install: true,
    subdir: 'csp/lib',
    install_tag: 'python-runtime',
)
# target_link_libraries(['cspstatsimpl', 'cspimpl', 'statsimpl'])
## Testlib c++ module
csptestlibimpl = py.extension_module(
    '_csptestlibimpl',
    'csptestlibimpl.cpp',
    dependencies: csp_engine,
    link_with: cspimpl,
    install: true,
    subdir: 'csp/lib',
    install_tag: 'python-runtime',
)
# target_link_libraries(['csptestlibimpl', 'cspimpl'])
## NumPy stats c++ module
npstatsimpl = static_library(
    'npstatsimpl',
    'npstatsimpl.cpp',
    include_directories: inc_np,
    dependencies: [csp_core, csp_engine, py.dependency()],
)
cspnpstatsimpl = py.extension_module(
    '_cspnpstatsimpl',
    'cspnpstatsimpl.cpp',
    include_directories: inc_np,
    link_with: [cspimpl, npstatsimpl],
    install: true,
    subdir: 'csp/lib',
    install_tag: 'python-runtime',
)
# target_link_libraries(['cspnpstatsimpl', 'cspimpl', 'npstatsimpl'])
# target_include_directories(['npstatsimpl', 'PRIVATE', numpy_include_dirs])
# target_include_directories(['cspnpstatsimpl', 'PRIVATE', numpy_include_dirs])
# install(['TARGETS', 'csptypesimpl', 'cspimpl', 'cspbaselibimpl', 'cspbasketlibimpl', 'cspmathimpl', 'cspstatsimpl', 'csptestlibimpl', 'cspnpstatsimpl', 'PUBLIC_HEADER', 'DESTINATION', 'include/csp/python', 'RUNTIME', 'DESTINATION', csp_runtime_install_subdir, 'LIBRARY', 'DESTINATION', 'lib/'])

py.install_sources('__init__.py', subdir: 'csp/lib')