# CMakeList.txt : CMake project for CMakeProjectWarnings, include source and define
# project specific logic here.
#
cmake_minimum_required (VERSION 3.8)

project ("CMakeProjectWarnings")

add_compile_options(/permissive- /Zc:wchar_t /Zc:forScope /Zc:inline /Zc:throwingNew)
add_compile_options(/Zc:alignedNew) # enable C++17 aligned-new support
add_compile_options(/WX /Wall) # enable all warnings as errors
add_compile_options(/utf-8) # enable UTF-8

# Disabled warnings:

# C4127 conditional expression is constant
# C4200 nonstandard extension used: zero-sized array in struct/union
# C4255 no function prototype given: converting '()' to '(void)
# C4275 non - DLL-interface class 'class_1' used as base for DLL-interface class 'class_2'
# C4355 'this': used in base member initializer list
# C4464 relative include path contains '..'
# C4514 unreferenced inline function has been removed
# C4623 default constructor was implicitly defined as deleted
# C4625 copy constructor was implicitly defined as deleted
# C4626 assignment operator was implicitly defined as deleted# C4668 not defined as a preprocessor macro
# C4710 function not inlined
# C4711 'function' selected for automatic inline expansion
# C4820 padding added after data member
# C4599 command line argument does not match precompiled header *** this happens because the precompiled header is generated with way less include files than one of our modules
# C5026 move constructor was implicitly defined as deleted
# C5027 move assignment operator was implicitly defined as deleted
# C5039 pointer or reference to potentially throwing function passed to extern C function under - EHc
# C5045 Compiler will insert Spectre mitigation for memory load if /Qspectre switch specified
# C5220 'name': a non-static data member with a volatile qualified type no longer implies that compiler generated copy/move constructors and copy/move assignment operators are not trivial
# C5246 'member': the initialization of a subobject should be wrapped in braces

add_compile_options(/wd4127 /wd4200 /wd4255 /wd4275 /wd4355 /wd4464 /wd4514 /wd4599 /wd4623 /wd4625 /wd4626 /wd4668 /wd4710 /wd4711 /wd4820 /wd5026 /wd5027 /wd5039 /wd5045 /wd5220 /wd5246)

# Add source to this project's executable.
add_executable (CMakeProjectWarnings "CMakeProjectWarnings.cpp" "CMakeProjectWarnings.h")

if (CMAKE_VERSION VERSION_GREATER 3.12)
  set_property(TARGET CMakeProjectWarnings PROPERTY CXX_STANDARD 20)
endif()

# TODO: Add tests and install targets if needed.
