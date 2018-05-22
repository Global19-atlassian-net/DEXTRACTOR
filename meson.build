project(
  'dextractor',
  'c',
  version : '0.0.1',
  default_options : [
    'buildtype=release',
    'warning_level=3',
    'c_std=gnu11',
    'b_ndebug=false'],
  license : 'BSD-3',
  meson_version : '>= 0.46.0')

############
# CXXFLAGS #
############

dextractor_flags = []
cc = meson.get_compiler('c')
foreach cflag: [
  '-Wno-unused-result',
  '-fno-strict-aliasing']
    if cc.has_argument(cflag)
      dextractor_flags += cflag
    endif
endforeach

################
# dependencies #
################

# dazzdb
dextractor_dazzdb_dep = dependency('dazzdb', fallback : ['dazzdb', 'dazzdb_dep'])

dextractor_deps = [dextractor_dazzdb_dep]

############
# binaries #
############

dextractor_exes = ['dexta', 'undexta']

foreach i : dextractor_exes
  executable(
    i,
    files([i + '.c']),
    dependencies : dextractor_deps,
    install : (not meson.is_subproject()),
    c_args : dextractor_flags)
endforeach
