# csp_autogen(['csp.impl.types.autogen_types', 'autogen_types', 'ENGINE_AUTOGEN_HEADER', 'ENGINE_AUTOGEN_SOURCE'])
csp_types_public_headers = ['CspEnum.h', 'CspType.h', 'DialectGenericType.h', 'PartialSwitchCspType.h', 'Struct.h', 'TypeCast.h']
csp_types_source_files = ['CspEnum.cpp', 'CspType.cpp', 'DialectGenericType.h', 'PartialSwitchCspType.h', 'Struct.cpp', 'TypeCast.h']
engine_public_headers = [engine_autogen_header, 'AdapterManager.h', 'AlarmInputAdapter.h', 'BasketInfo.h', 'ConstInputAdapter.h', 'Consumer.h', 'CppNode.h', 'CycleStepTable.h', 'Dictionary.h', 'DynamicEngine.h', 'DynamicNode.h', 'Engine.h', 'Enums.h', 'EventPropagator.h', 'Feedback.h', 'GraphOutputAdapter.h', 'InputAdapter.h', 'InputId.h', 'Node.h', 'OutputAdapter.h', 'PendingPushEvents.h', 'Profiler.h', 'PushEvent.h', 'PullInputAdapter.h', 'PushInputAdapter.h', 'PushPullInputAdapter.h', 'RootEngine.h', 'Scheduler.h', 'StatusAdapter.h', 'TickBuffer.h', 'TimerInputAdapter.h', 'TimeSeries.h', 'TimeSeriesProvider.h', 'VectorContainer.h', 'WindowBuffer.h']
engine_source_files = [engine_autogen_source, 'AdapterManager.cpp', 'BasketInfo.cpp', 'Consumer.cpp', 'CycleStepTable.cpp', 'Dictionary.cpp', 'DynamicEngine.cpp', 'DynamicNode.cpp', 'Engine.cpp', 'Enums.cpp', 'EventPropagator.cpp', 'GraphOutputAdapter.cpp', 'InputAdapter.cpp', 'Node.cpp', 'OutputAdapter.cpp', 'PendingPushEvents.cpp', 'PushPullInputAdapter.cpp', 'RootEngine.cpp', 'Scheduler.cpp', 'StatusAdapter.cpp', 'TimeSeries.cpp', 'TimeSeriesProvider.cpp', 'VectorContainer.cpp', engine_public_headers]
csp_types_lib = static_library('csp_types', csp_types_source_files)
# set_target_properties(['csp_types', 'PROPERTIES', 'PUBLIC_HEADER', '${CSP_TYPES_PUBLIC_HEADERS}'])
csp_engine_lib = static_library('csp_engine', engine_source_files)
# set_target_properties(['csp_engine', 'PROPERTIES', 'PUBLIC_HEADER', '${ENGINE_PUBLIC_HEADERS}'])
# target_link_libraries(['csp_engine', 'csp_core', 'csp_types'])
# install(['FILES', csp_types_public_headers, engine_public_headers, 'DESTINATION', 'include/csp/engine'])
# install(['TARGETS', 'csp_types', 'csp_engine', 'PUBLIC_HEADER', 'DESTINATION', 'include/csp/engine', 'RUNTIME', 'DESTINATION', csp_runtime_install_subdir, 'LIBRARY', 'DESTINATION', 'lib/'])
