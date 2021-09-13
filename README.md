1. Setup Msys as described here https://www.msys2.org/
2. Put bazel.exe on your system path
  - Set: `BAZEL_SH={MSYS_INSTALL}\usr\bin\bash.exe`
3. Run: `bazel --compiler=mingw-gcc build ...`
