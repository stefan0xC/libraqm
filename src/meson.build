src_dir = include_directories('.')

sources = [
  'raqm.c',
  'raqm.h'
  ]

install_headers('raqm.h')

mapfile = 'raqm.map'
vflag = '-Wl,--version-script,@0@/@1@'.format(meson.current_source_dir(), mapfile)

raqm = shared_library(
  'raqm', sources,
  soversion: soversion,
  version: library_version,
  dependencies : deps,
  include_directories : src_dir,
  link_args : ['-Wl,--no-undefined', vflag],
  link_depends : mapfile,
  install : true)

raqm_test = shared_library(
  'raqm_test', sources,
  soversion: soversion,
  version: library_version,
  dependencies : deps,
  include_directories : src_dir,
  c_args : '-DRAQM_TESTING=true',
  link_args : ['-Wl,--no-undefined', vflag],
  link_depends : mapfile,
  install : false)
