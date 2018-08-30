project('libraqm', 'c', version : '0.6.0')

# Project version:
version = meson.project_version()
version_array = version.split('.')
major_version = version_array[0].to_int()
minor_version = version_array[1].to_int()
micro_version = version_array[2].to_int()

# Libtool version: current:revision:age
interface_age = micro_version
binary_age = 100 * minor_version + micro_version
soversion = major_version
# current = minor * 100 + micro
library_version = '@0@.@1@.@2@'.format(soversion, binary_age - interface_age, interface_age)

# Dependencies:
freetype = dependency('freetype2', version : '>= 12.0.6')
harfbuzz = dependency('harfbuzz')
fribidi = dependency('fribidi')

deps = [freetype, harfbuzz, fribidi]

gtkdoc = find_program('gtkdoc-scan', required: false)
if gtkdoc.found()
  gnome = import('gnome')
  subdir('docs')
endif
subdir('src')
subdir('tests')

pkg = import('pkgconfig')
pkg.generate(libraries: raqm,
  version: version,
  name: 'Raqm',
  filebase: 'raqm',
  description: 'A library for complex text layout.',
  url: 'https://github.com/HOST-Oman/libraqm',
  requires: freetype,
  requires_private: [harfbuzz, fribidi]
  )
