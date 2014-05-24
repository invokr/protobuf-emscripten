# protobuf-emscripten


## About

This repository implements the nessecary code for protobuf to run via emscripten.

## Compiling

The following instructions are for Unix based systems. Compiling on Windows should also work but has not been tested.

 - Clone the repository
 - Install autotools and emscripten
 - `sh autogen.sh` 
 - `emconfigure ./configure`
 - `emmake make`

After the last command has generated the shared libraries under src/.libs it will try to execute lt-protoc and fail. This is not a problem but to be expected because the binary in question only contains LLVM-Bytecode. At this point `libprotobuf.so` has already been build and is ready to be used in your project.

*Important:* The protoc binary build with `emmake` is not usable. Because the generated code does not need to be changed, you can just use any protoc. 

## License

For protobuf, see license.txt. I place my changes to the code in the public domain.
