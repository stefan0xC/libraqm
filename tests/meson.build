test_dir = include_directories('.')

test_files = [
  'buffer-flags-1.test',
  'direction-ltr-1.test',
  'direction-ltr-2.test',
  'direction-ltr-3.test',
  'direction-ltr-4.test',
  'direction-ltr-5.test',
  'direction-rtl-1.test',
  'direction-rtl-2.test',
  'direction-rtl-3.test',
  'direction-rtl-4.test',
  'direction-rtl-5.test',
  'empty-text.test',
  'features-arabic.test',
  'features-kerning.test',
  'features-ligature.test',
  'scripts-backward.test',
  'scripts-backward-ltr.test',
  'scripts-backward-rtl.test',
  'scripts-forward.test',
  'scripts-forward-ltr.test',
  'scripts-forward-rtl.test',
  'languages-sr.test',
  'languages-sr-ru.test',
  'multi-fonts.test',
  'multi-fonts2.test',
  'xyoffset.test',
  'test1.test',
  'test2.test',
  'test3.test',
  'test4.test',
  'test5.test',
  'cursor_position1.test',
  'cursor_position2.test',
  'cursor_position3.test',
  'cursor_position4.test',
  'cursor_position_GB3.test',
  'cursor_position_GB4.test',
  'cursor_position_GB5.test',
  'cursor_position_GB8a.test',
  'cursor_position_GB9.test',
  'cursor_position_GB9a.test'
  ]
#configure_file(input: 'runtest.py', output: 'runtest.py', copy: true)
subdir('fonts/sha1sum')

selftest = executable(
  'raqm-test', 'raqm-test.c',
  dependencies: deps,
  include_directories: src_dir,
  link_with: raqm_test
  )

runtest = find_program('runtest.py')
foreach test_file: test_files
  # copy test-file to build_directory
  file = configure_file( input: test_file, output: test_file, copy: true)
  test(
    test_file.split('.')[0],
    runtest,
    workdir: meson.current_build_dir(),
    depends: selftest,
    args: [ test_file, ],
    )
endforeach
