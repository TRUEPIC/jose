cd = configuration_data()
cd.set('VERSION', meson.project_version())
configure_file(
  input: 'jose.h.in',
  output: 'jose.h',
  configuration: cd
)

libjose_inc = include_directories('..')

install_headers(
  '../cmd/jose.h',
  'cfg.h',
  'io.h',
  'b64.h',
  'jwk.h',
  'jws.h',
  'jwe.h',
  'openssl.h',
  subdir: meson.project_name()
)
