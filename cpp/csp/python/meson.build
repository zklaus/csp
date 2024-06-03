# types library
csptypesimpl_public_headers = ['CspTypeFactory.h', 'PyCspEnum.h', 'PyCspType.h', 'PyStruct.h', 'PyStructList.h', 'PyStructList_impl.h', 'PyStructFastList.h', 'PyStructFastList_impl.h', 'VectorWrapper.h']
csptypesimpl_lib = library('csptypesimpl', 'csptypesimpl.cpp', 'CspTypeFactory.cpp', 'PyCspEnum.cpp', 'PyCspType.cpp', 'PyStruct.cpp', 'PyStructToJson.cpp')
# set_target_properties(['csptypesimpl', 'PROPERTIES', 'PUBLIC_HEADER', '${CSPTYPESIMPL_PUBLIC_HEADERS}'])
# target_compile_definitions(['csptypesimpl', 'PUBLIC', 'RAPIDJSON_HAS_STDSTRING=1'])
# target_link_libraries(['csptypesimpl', 'csp_core', 'csp_types'])
# target_compile_definitions(['csptypesimpl', 'PRIVATE', 'CSPTYPESIMPL_EXPORTS=1'])
cspimpl_public_headers = ['Common.h', 'Conversions.h', 'Exception.h', 'InitHelper.h', 'NumpyConversions.h', 'NumpyInputAdapter.h', 'PyAdapterManagerWrapper.h', 'PyBasketInputProxy.h', 'PyBasketOutputProxy.h', 'PyCppNode.h', 'PyEngine.h', 'PyInputAdapterWrapper.h', 'PyInputProxy.h', 'PyIterator.h', 'PyCppNode.h', 'PyNode.h', 'PyNodeWrapper.h', 'PyNumbaNode.h', 'PyObjectPtr.h', 'PyOutputAdapterWrapper.h', 'PyOutputProxy.h', 'PyConstants.h', 'PyStructToJson.h']
cspimpl_lib = shared_library('cspimpl', 'cspimpl.cpp', 'Conversions.cpp', 'NumpyConversions.cpp', 'PyAdapterManager.cpp', 'PyAdapterManagerWrapper.cpp', 'PyConstAdapter.cpp', 'PyCppNode.cpp', 'PyEngine.cpp', 'PyGraphOutputAdapter.cpp', 'PyInputAdapterWrapper.cpp', 'PyBasketInputProxy.cpp', 'PyBasketOutputProxy.cpp', 'PyDynamicNode.cpp', 'PyFeedbackAdapter.cpp', 'PyInputProxy.cpp', 'PyNode.cpp', 'PyNodeWrapper.cpp', 'PyNumbaNode.cpp', 'PyNumpyAdapter.cpp', 'PyOutputAdapter.cpp', 'PyOutputAdapterWrapper.cpp', 'PyOutputProxy.cpp', 'PyPullInputAdapter.cpp', 'PyPushInputAdapter.cpp', 'PyPushPullInputAdapter.cpp', 'PyManagedSimInputAdapter.cpp', 'PyTimerAdapter.cpp', 'PyConstants.cpp', cspimpl_public_headers)
# set_target_properties(['cspimpl', 'PROPERTIES', 'PUBLIC_HEADER', '${CSPIMPL_PUBLIC_HEADERS}'])
# target_link_libraries(['cspimpl', 'csptypesimpl', 'csp_core', 'csp_engine'])
# target_compile_definitions(['cspimpl', 'PUBLIC', 'NPY_NO_DEPRECATED_API=NPY_1_7_API_VERSION'])
# target_compile_definitions(['cspimpl', 'PRIVATE', 'CSPIMPL_EXPORTS=1'])
## Baselib c++ module
cspbaselibimpl_lib = shared_library('cspbaselibimpl', 'cspbaselibimpl.cpp')
# target_link_libraries(['cspbaselibimpl', 'cspimpl', 'baselibimpl'])
# Include exprtk include directory for exprtk node
# target_include_directories(['cspbaselibimpl', 'PRIVATE', exprtk_include_dirs])
## Basketlib c++ module
cspbasketlibimpl_lib = shared_library('cspbasketlibimpl', 'cspbasketlibimpl.cpp')
# target_link_libraries(['cspbasketlibimpl', 'cspimpl', 'basketlibimpl'])
## Math c++ module
cspmathimpl_lib = shared_library('cspmathimpl', 'cspmathimpl.cpp')
# target_link_libraries(['cspmathimpl', 'cspimpl', 'mathimpl'])
## Stats c++ module
cspstatsimpl_lib = shared_library('cspstatsimpl', 'cspstatsimpl.cpp')
# target_link_libraries(['cspstatsimpl', 'cspimpl', 'statsimpl'])
## Testlib c++ module
csptestlibimpl_lib = shared_library('csptestlibimpl', 'csptestlibimpl.cpp')
# target_link_libraries(['csptestlibimpl', 'cspimpl'])
## NumPy stats c++ module
npstatsimpl_lib = static_library('npstatsimpl', 'npstatsimpl.cpp')
cspnpstatsimpl_lib = shared_library('cspnpstatsimpl', 'cspnpstatsimpl.cpp')
# target_link_libraries(['cspnpstatsimpl', 'cspimpl', 'npstatsimpl'])
# target_include_directories(['npstatsimpl', 'PRIVATE', numpy_include_dirs])
# target_include_directories(['cspnpstatsimpl', 'PRIVATE', numpy_include_dirs])
# install(['TARGETS', 'csptypesimpl', 'cspimpl', 'cspbaselibimpl', 'cspbasketlibimpl', 'cspmathimpl', 'cspstatsimpl', 'csptestlibimpl', 'cspnpstatsimpl', 'PUBLIC_HEADER', 'DESTINATION', 'include/csp/python', 'RUNTIME', 'DESTINATION', csp_runtime_install_subdir, 'LIBRARY', 'DESTINATION', 'lib/'])
