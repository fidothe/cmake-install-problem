# Minimal repro for my problem getting CMake to install headers

I would expect the invocation of `install()` with
```
install(TARGETS gubbins FILE_SET HEADERS)
```

to result in the `HEADERS` file set associated with the `gubbins` target to be installed, along with the shared library that is built.

I'm having this problem in a real project, and have created this trivial one to illustrate the problem.

This is not happening, and only the library files are being installed when I invoke `cmake --install` with a `--prefix`. (The same happens if I omit `--prefix` but have set `CMAKE_INSTALL_PREFIX` in `CMakeLists.txt`)

I'm assuming I'm doing something daft, but I'm at a loss for what...