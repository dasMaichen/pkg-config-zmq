pkg_config = read_config('pkg_config', 'path', 'pkg-config')

genrule(
  name = 'preprocessor-flags',
  out = 'out.txt',
  cmd = pkg_config + ' libzmq --cflags > $OUT',
)

genrule(
  name = 'linker-flags',
  out = 'out.txt',
  cmd = pkg_config + ' libzmq --libs > $OUT',
)

prebuilt_cxx_library(
  name = 'zmq',
  header_namespace = '',
  header_only = True,
  exported_preprocessor_flags = [
    '@$(location :preprocessor-flags)',
  ],
  exported_linker_flags = [
    '@$(location :linker-flags)',
  ],
  visibility = [
    'PUBLIC',
  ],
)
