  # csp_autogen(['csp.adapters.websocket_types', 'websocket_types', 'WEBSOCKET_HEADER', 'WEBSOCKET_SOURCE'])
  ws_client_header_files = ['ClientAdapterManager.h', 'ClientInputAdapter.h', 'ClientOutputAdapter.h', 'ClientHeaderUpdateAdapter.h', 'WebsocketEndpoint.h', websocket_header]
  ws_client_source_files = ['ClientAdapterManager.cpp', 'ClientInputAdapter.cpp', 'ClientOutputAdapter.cpp', 'ClientHeaderUpdateAdapter.cpp', 'WebsocketEndpoint.cpp', ws_client_header_files, websocket_source]
  csp_websocket_client_adapter_lib = static_library('csp_websocket_client_adapter', ws_client_source_files)
  # set_target_properties(['csp_websocket_client_adapter', 'PROPERTIES', 'PUBLIC_HEADER', '${WS_CLIENT_SOURCE_FILES}'])
  Boost_dep = dependency('Boost')
  OpenSSL_dep = dependency('OpenSSL')
  # target_link_libraries(['csp_websocket_client_adapter', 'PRIVATE', 'csp_adapter_utils', 'Boost::boost', 'OpenSSL::SSL'])
  # install(['TARGETS', 'csp_websocket_client_adapter', 'PUBLIC_HEADER', 'DESTINATION', 'include/csp/adapters/websocket', 'RUNTIME', 'DESTINATION', csp_runtime_install_subdir, 'LIBRARY', 'DESTINATION', 'lib/'])
