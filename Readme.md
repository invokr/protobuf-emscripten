About
-----

Emscripten port of Google's Protobuf library.

Building
--------

    cd [2.6.1|3.1.0]
    sh autogen.sh
    emconfigure ./configure
    emmake Make

This will generate a dynamic library in `src/.libs/` called `libprotobuf.$(VERSION).[so|dylib]`.
Though the suffix suggests that this is a regular dylib, it contains emscripten bytecode.
Change the suffix to `.bc` and you'll be able to link it into your emscripten project.

The `protoc` compiler will not be build but any code generate by the standard `protoc` is compatible
with emscripten.

License
-------

Protobuf: Original license

Patches: Public Domain
