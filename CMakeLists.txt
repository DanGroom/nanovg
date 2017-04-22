cmake_minimum_required(VERSION 3.7)
project(nanovg)
find_package(OpenGL REQUIRED)
set(CMAKE_CXX_STANDARD 11)

set(SOURCE_FILES
#    example/demo.c
#    example/demo.h
#    example/example_fbo.c
#    example/example_gl2.c
#    example/example_gl3.c
#    example/example_gles2.c
#    example/example_gles3.c
#    example/perf.c
#    example/perf.h
#    example/stb_image_write.h
#    obsolete/nanovg_gl2.h
#    obsolete/nanovg_gl3.h
    src/fontstash.h
    src/nanovg.c
    src/nanovg.h
    src/nanovg_gl.h
    src/nanovg_gl_utils.h
    src/stb_image.h
    src/stb_truetype.h)

add_library(nanovg ${SOURCE_FILES})

include_directories(src)
add_library(demo example/demo.c example/perf.c)

link_libraries(nanovg demo glfw ${OPENGL_LIBRARIES})
add_executable(example_gl2 example/example_gl2.c)
add_executable(example_gl3 example/example_gl3.c)
add_executable(example_fbo example/example_fbo.c)
add_executable(example_gles2 example/example_gles2.c)
add_executable(example_gles3 example/example_gles3.c)