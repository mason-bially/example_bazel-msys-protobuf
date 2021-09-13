1. Setup Msys as described here https://www.msys2.org/
2. Put bazel.exe on your system path
    - Set: `BAZEL_SH={MSYS_INSTALL}\usr\bin\bash.exe`
3. Run: `bazel build --compiler=mingw-gcc ...` (or `test`, or `run` the `src:client` or `src:server`)
