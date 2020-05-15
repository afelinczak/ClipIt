cmake_minimum_required(VERSION 3.16)
project(ClipIt C)

set(CMAKE_C_STANDARD 11)

include_directories(.)
include_directories(src)
include_directories(/usr/include/libayatana-appindicator3-0.1/)

add_executable(ClipIt
        src/clipit-i18n.h
        src/daemon.c
        src/daemon.h
        src/eggaccelerators.c
        src/eggaccelerators.h
        src/history.c
        src/history.h
        src/keybinder.c
        src/keybinder.h
        src/main.c
        src/main.h
        src/manage.c
        src/manage.h
        src/preferences.c
        src/preferences.h
        src/utils.c
        src/utils.h
        config.h)

# Use the package PkgConfig to detect GTK+ headers/library files
FIND_PACKAGE(PkgConfig REQUIRED)

find_package(X11 REQUIRED)
link_libraries(${X11_LIBRARIES})


# Setting up Intl
find_package (Intl REQUIRED)
find_package(Gettext REQUIRED)
link_libraries(${Intl_LIBRARIES})
include_directories(${INTL_INCLUDE_DIRS})
link_directories(${INTL_LIBRARY_DIRS})

add_definitions(-DCLIPITLOCALEDIR="/usr/local/share")
add_definitions(-DHAVE_CONFIG_H=1)

PKG_CHECK_MODULES(APPINDICATOR ayatana-appindicator3-0.1)
SET(HAVE_AYATANAAPPINDICATOR 1)
SET(HAVE_APPINDICATOR 1)

INCLUDE_DIRECTORIES(${APPINDICATOR_INCLUDE_DIRS})
LINK_DIRECTORIES(${APPINDICATOR_LIBRARY_DIRS})
ADD_DEFINITIONS(${APPINDICATOR_CFLAGS})


PKG_CHECK_MODULES(GTK3 REQUIRED gtk+-3.0)

# Setup CMake to use GTK+, tell the compiler where to look for headers
# and to the linker where to look for libraries
INCLUDE_DIRECTORIES(${GTK3_INCLUDE_DIRS})
LINK_DIRECTORIES(${GTK3_LIBRARY_DIRS})

# Add other flags to the compiler
ADD_DEFINITIONS(${GTK3_CFLAGS_OTHER})

# Link the target to the GTK+ libraries
TARGET_LINK_LIBRARIES(ClipIt ${GTK3_LIBRARIES})
target_link_libraries(ClipIt ${X11_LIBRARIES})
TARGET_LINK_LIBRARIES(ClipIt ${APPINDICATOR_LIBRARIES})