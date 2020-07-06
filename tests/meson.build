scripts = [
  'jose-alg',
  'jose-fmt',
  'jose-b64-enc',
  'jose-b64-dec',
  'jose-jwk-eql',
  'jose-jwk-exc',
  'jose-jwk-gen',
  'jose-jwk-pub',
  'jose-jwk-use',
  'jose-jwk-thp',
  'jose-jws-fmt',
  'jose-jws-ver',
  'jose-jws-sig',
  'jose-jwe-fmt',
  'jose-jwe-dec',
  'jose-jwe-enc',
]

progs = [
  'alg_hash',
  'alg_sign',
  'alg_encr',
  'alg_wrap',
  'alg_comp',
  'api_b64',
  'api_jws',
  'api_jwe',
]

e = environment()
e.append('PATH', meson.current_build_dir() + '/../cmd', separator: ':')
e.set('VECTORS', meson.current_source_dir() + '/vectors')

openmp = dependency('OpenMP')

foreach p: progs
  if p == 'api_b64'
    dep = [jansson, openmp]
    to = 1800
  else
    dep = jansson
    to = 30
  endif
  exe = executable(p, sources: [p + '.c'],
    include_directories:libjose_inc,
    dependencies: dep,
    link_with: libjose)
  test(p, exe, timeout: to)
endforeach

foreach s: scripts
  exe = find_program('./' + s)
  test(s, exe, env: e, timeout: 60)
endforeach
