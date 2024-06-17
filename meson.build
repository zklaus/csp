project(
    'csp',
    'c',
    'cpp',
    license: 'MIT',
    version: '0.0.4',
    subproject_dir: 'cpp',
)

py = import('python').find_installation(pure: false)

incdir_numpy = run_command(py,
  ['-c', 'import os; os.chdir(".."); import numpy; print(numpy.get_include())'],
  check : true
).stdout().strip()

inc_np = include_directories(incdir_numpy)


cmake = import('cmake')
opt_var = cmake.subproject_options()
opt_var.add_cmake_defines({
    'CSP_USE_VCPKG': false,
    'Python_EXECUTABLE': py.path(),
    'CSP_PYTHON_VERSION': py.language_version(),
    'CSP_BUILD_NO_CXX_ABI': false,
    'CSP_BUILD_TESTS': false,
    'CSP_MANYLINUX': false,
    'CSP_BUILD_KAFKA_ADAPTER': true,
    'CSP_BUILD_PARQUET_ADAPTER': true,
    'CSP_BUILD_WS_CLIENT_ADAPTER': true,
})
opt_var.set_override_option('name_prefix', '_')

sub_proj = cmake.subproject('csp', options: opt_var)

baselibimpl = sub_proj.dependency('baselibimpl')
basketlibimpl = sub_proj.dependency('basketlibimpl')
csp_core = sub_proj.dependency('csp_core')
csp_engine = sub_proj.dependency('csp_engine')
csp_types = sub_proj.dependency('csp_types')
mathimpl = sub_proj.dependency('mathimpl')
statsimpl = sub_proj.dependency('statsimpl')

subdir('csp')
