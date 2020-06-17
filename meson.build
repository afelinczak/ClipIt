project('ClipIt', 'c', version : '1.4.5',)

headers = [
    'src/clipit-i18n.h',
    'src/daemon.h',
    'src/eggaccelerators.h',
    'src/history.h',
    'src/keybinder.h',
    'src/main.h',
    'src/manage.h',
    'src/preferences.h',
    'src/utils.h'
]
install_headers(headers)

sources = [
        'src/daemon.c',
        'src/eggaccelerators.c',
        'src/history.c',
        'src/keybinder.c',
        'src/main.c',
        'src/manage.c',
        'src/preferences.c',
        'src/utils.c'
]

#meson configure -Doption=newvalue
if get_option('with-gtk3')
  gtk = 'gtk+-3.0'
  app_ind = 'ayatana-appindicator3-0.1'
else
  gtk = 'gtk+-2.0'
  app_ind = 'ayatana-appindicator-0.1'
endif

dependencies = [
    dependency('glib-2.0'),
    dependency('x11'),
    dependency(gtk),
    dependency(app_ind)
]

subdir('po')

conf = configuration_data()

if get_option('enable-appindicator')
  conf.set('HAVE_APPINDICATOR', 1)
else
  conf.set('HAVE_APPINDICATOR', 0)
endif

package = 'clipit'
conf.set('ENABLE_NLS', 1)
conf.set_quoted('GETTEXT_PACKAGE', package)
conf.set('HAVE_BIND_TEXTDOMAIN_CODESET', 1)
conf.set('HAVE_DCGETTEXT', 1)
conf.set('HAVE_GETTEXT', 1)
conf.set('HAVE_INTTYPES_H', 1)
conf.set('HAVE_LC_MESSAGES', 1)
conf.set('HAVE_LOCALE_H', 1)
conf.set('HAVE_MEMORY_H', 1)
conf.set('HAVE_STDINT_H', 1)
conf.set('HAVE_STDLIB_H', 1)
conf.set('HAVE_STRINGS_H', 1)
conf.set('HAVE_STRING_H', 1)
conf.set('HAVE_SYS_STAT_H', 1)
conf.set('HAVE_SYS_TYPES_H', 1)
conf.set('HAVE_UNISTD_H', 1)
conf.set_quoted('PACKAGE', package)
conf.set_quoted('PACKAGE_BUGREPORT', 'oss@rspwn.com')
conf.set_quoted('PACKAGE_NAME', package)
conf.set_quoted('PACKAGE_STRING', package + ' ' + meson.project_version())
conf.set_quoted('PACKAGE_TARNAME', package)
conf.set_quoted('PACKAGE_URL', '')
conf.set_quoted('PACKAGE_VERSION', meson.project_version())
conf.set('STDC_HEADERS', 1)
conf.set_quoted('VERSION', meson.project_version())

configure_file(output : 'config.h', configuration : conf)
               
executable('ClipIt', sources, install : true, dependencies: dependencies)
