project('jose', 'c', license: 'APL2', version: '10',
  default_options: [
    'c_std=gnu99',
    ])

zlib = dependency('zlib')
#threads = dependency('threads')
jansson = dependency('jansson', version: '>=2.10')
libcrypto = dependency('libcrypto', version: '>=1.0.2')

subdir('jose')
subdir('doc')
subdir('lib')
subdir('cmd')
subdir('tests')

pkg = import('pkgconfig')
pkg.generate(
  description: 'Library for managing JOSE objects',
  version: meson.project_version(),
  filebase: meson.project_name(),
  name: 'José Library',

  requires_private: [ 'zlib', 'libcrypto' ],
  libraries: libjose,
  requires: 'jansson',
)
