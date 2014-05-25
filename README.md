# protobuf-emscripten

This is a version of protobuf that has been patched to support compliation via emscripten.

## Compiling

The following instructions are for Unix based systems. Compiling on Windows should also work but has not been tested yet.

 - Clone the repository
 - Install autotools and emscripten
 - `sh autogen.sh` 
 - `emconfigure ./configure`
 - `emmake make`

After the last command has generated the shared libraries under src/.libs, it will fail executing lt-protoc. This is to be expected because the binary in question only contains LLVM-Bytecode. At this point `libprotobuf.so` has already been build and is ready to be used in your project.

*Important:* The protoc binary build with `emmake` is not usable. Please use a seperate protoc that has been build with a C++ compiler.

## License

For protobuf, see license.txt. I place my changes to the code in the public domain.
