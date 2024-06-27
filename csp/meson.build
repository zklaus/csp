py.install_sources(
    'baselib.py',
    'basketlib.py',
    'curve.py',
    'dataframe.py',
    '__init__.py',
    'math.py',
    'profiler.py',
    'random.py',
    'showgraph.py',
    'stats.py',
    'typing.py',
    subdir: 'csp',
)

pure_subdirs = [
    'adapters',
    'impl',
    'utils',
]

csp_dir = py.get_install_dir() / 'csp'

foreach subdir: pure_subdirs
  install_subdir(subdir, install_dir: csp_dir, install_tag: 'python-runtime')
endforeach

install_subdir('tests', install_dir: csp_dir, install_tag: 'tests')

subdir('lib')