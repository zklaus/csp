if 'CSP_BUILD_KAFKA_ADAPTER'
  kafkaadapterimpl_lib = shared_library('kafkaadapterimpl', 'kafkaadapterimpl.cpp')
  # target_link_libraries(['kafkaadapterimpl', 'csp_core', 'csp_engine', 'cspimpl', 'csp_kafka_adapter'])
  # install(['TARGETS', 'kafkaadapterimpl', 'RUNTIME', 'DESTINATION', csp_runtime_install_subdir])
endif
if 'CSP_BUILD_PARQUET_ADAPTER'
  vendored_pyarrow_root = '${CMAKE_SOURCE_DIR}/cpp/csp/python/adapters/vendored/pyarrow-16.0.0/'
  arrow_python_srcs = [vendored_pyarrow_root, '/arrow/python/arrow_to_pandas.cc', vendored_pyarrow_root, '/arrow/python/benchmark.cc', vendored_pyarrow_root, '/arrow/python/common.cc', vendored_pyarrow_root, '/arrow/python/datetime.cc', vendored_pyarrow_root, '/arrow/python/decimal.cc', vendored_pyarrow_root, '/arrow/python/deserialize.cc', vendored_pyarrow_root, '/arrow/python/extension_type.cc', vendored_pyarrow_root, '/arrow/python/gdb.cc', vendored_pyarrow_root, '/arrow/python/helpers.cc', vendored_pyarrow_root, '/arrow/python/inference.cc', vendored_pyarrow_root, '/arrow/python/init.cc', vendored_pyarrow_root, '/arrow/python/io.cc', vendored_pyarrow_root, '/arrow/python/ipc.cc', vendored_pyarrow_root, '/arrow/python/numpy_convert.cc', vendored_pyarrow_root, '/arrow/python/numpy_to_arrow.cc', vendored_pyarrow_root, '/arrow/python/python_to_arrow.cc', vendored_pyarrow_root, '/arrow/python/pyarrow.cc', vendored_pyarrow_root, '/arrow/python/serialize.cc', vendored_pyarrow_root, '/arrow/python/csv.cc', vendored_pyarrow_root, '/arrow/python/filesystem.cc']
  parquetadapterimpl_lib = shared_library('parquetadapterimpl', 'parquetadapterimpl.cpp', arrow_python_srcs)
  # target_link_libraries(['parquetadapterimpl', 'csp_core', 'csp_engine', 'cspimpl', 'csp_parquet_adapter'])
  # target_include_directories(['parquetadapterimpl', 'PUBLIC', arrow_include_dir, parquet_include_dir, '${VENDORED_PYARROW_ROOT}'])
  # target_compile_definitions(['parquetadapterimpl', 'PUBLIC', 'ARROW_PYTHON_STATIC'])
  # install(['TARGETS', 'parquetadapterimpl', 'RUNTIME', 'DESTINATION', csp_runtime_install_subdir])
endif
if 'CSP_BUILD_WS_CLIENT_ADAPTER'
  cmake_cxx_standard = '17'
  websocketadapterimpl_lib = shared_library('websocketadapterimpl', 'websocketadapterimpl.cpp')
  # target_link_libraries(['websocketadapterimpl', 'csp_core', 'csp_engine', 'cspimpl', 'csp_websocket_client_adapter'])
  # install(['TARGETS', 'websocketadapterimpl', 'RUNTIME', 'DESTINATION', csp_runtime_install_subdir])
  cmake_cxx_standard = '20'
endif
