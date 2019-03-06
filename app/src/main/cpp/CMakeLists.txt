cmake_minimum_required(VERSION 3.4.1)

add_definitions("-DKTX_OPENGL_ES3 -DSUPPORT_SOFTWARE_ETC_UNPACK=0")

include_directories(libktx)
include_directories(stb)

add_library( # Sets the name of the library.
        textureloader

        # Sets the library as a shared library.
        SHARED

        # Provides a relative path to your source file(s).
        libktx/checkheader.c
        libktx/errstr.c
        libktx/hashtable.c
        libktx/loader.c
        libktx/swap.c
        libktx/writer.c
        stb/stb_image.c
        file.c
        jni_main.c
        texture.c)

find_library( # Sets the name of the path variable.
        log-lib

        # Specifies the name of the NDK library that
        # you want CMake to locate.
        log)

# Specifies libraries CMake should link to your target library. You
# can link multiple libraries, such as libraries you define in this
# build script, prebuilt third-party libraries, or system libraries.

target_link_libraries( # Specifies the target library.
        textureloader

        android
        GLESv3
        EGL
        # Links the target library to the log library
        # included in the NDK.
        ${log-lib})