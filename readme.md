# QuickJS

QuickJS is a small and embeddable Javascript engine written in C89. 

### Comparisons
| File |  Size Mb |
| ------ | ------ |
| Quickjs| 1 |
| PKG NodeJs  | 33 |
| Deno     | 59 |
| Electron SDK     | 215 |
| NWjs SDK     | 362 |


It was created by Charlie Gordon and Fabrice Bellard creator of FFMPEG and QEMU.

It supports the ES2020 specification including modules, asynchronous generators, proxies and BigInt.

It optionally supports mathematical extensions such as:
- big decimal floating point numbers (BigDecimal)
- big binary floating point numbers (BigFloat) 
- and operator overloading.

-----------

Official site: https://bellard.org/quickjs/

The main documentation is in doc/quickjs.pdf or doc/quickjs.html.

-----------
### Main Features:

- Small and easily embeddable: just a few C files, no external dependency, 210 KiB of x86 code for a simple hello world program.
- Fast interpreter with very low startup time: runs the 75000 tests of the ECMAScript Test Suite in about 100 seconds on a single core of a desktop PC. The complete life cycle of a runtime instance completes in less than 300 microseconds.
- Almost complete ES2020 support including modules, asynchronous generators and full Annex B support (legacy web compatibility).
- Passes nearly 100% of the ECMAScript Test Suite tests when selecting the ES2020 features. A summary is available at Test262 Report.
- Can compile Javascript sources to executables with no external dependency.
- Garbage collection using reference counting (to reduce memory usage and have deterministic behavior) with cycle removal.
- Mathematical extensions: BigDecimal, BigFloat, operator overloading, bigint mode, math mode.
- Command line interpreter with contextual colorization implemented in Javascript.
- Small built-in standard library with C library wrappers.


-----------

## QUICKJS TUTORIALS
 
### 1. How Build in Windows
https://github.com/Gurigraphics/quickjs/wiki/01.-How-Build-Windows

### 2. Hello World Binary File
https://github.com/Gurigraphics/quickjs/wiki/02.-Hello-World-Binary-File

### 3. How import and run a Javascript Module
https://github.com/Gurigraphics/quickjs/wiki/03.-How-import-and-run-a-Javascript-Module

### 4. How import and run a C Module
https://github.com/Gurigraphics/quickjs/wiki/04.-How-import-and-run-a-C-Module

### 5. How get CMD args
https://github.com/Gurigraphics/quickjs/wiki/05.-How-get-CMD-args

### 6. How Create a C Module
https://github.com/Gurigraphics/quickjs/wiki/06.-How-Create-a-C-Module

### 7. Module STD Methods
https://github.com/Gurigraphics/quickjs/wiki/07.-Module-STD-Methods

### 8. Module OS Methods
https://github.com/Gurigraphics/quickjs/wiki/08.-Module-OS-Methods

### 09. Creating and Using an DLL or SO in C
https://github.com/Gurigraphics/quickjs/wiki/09.-Creating-and-Using-an-DLL-or-SO

### 10. Creating and Using an Import Library in C
https://github.com/Gurigraphics/quickjs/wiki/10.-Creating-and-Using-an-Import-Library

### 11. Call a JS function from the C side
https://github.com/Gurigraphics/quickjs/wiki/11.--Call-a-JS-function-from-the-C-side

### 12. Call a C function from the JS side
https://github.com/Gurigraphics/quickjs/wiki/12.-Call-a-C-function-from-the-JS-side

### 13. Initialize and get args
https://github.com/Gurigraphics/quickjs/wiki/13.-Initialize-and-get-args

### 14. Quickjs and Raylib
https://github.com/Gurigraphics/quickjs/wiki/14.Quickjs-and-Raylib
 
-----------

### References
| File |  Repository |
| ------ | ------ |
| Makefile - Windows 64bits | https://github.com/mengmo/QuickJS-Windows-Build |
| Writing native modules in C for QuickJS engine | https://calbertts.medium.com/writing-native-modules-in-c-for-quickjs-engine-49043587f2e2 |


-----------

### Related Projects

txiki.js - Node modules
https://github.com/saghul/txiki.js

quickjs-emscripten - Javascript/Typescript bindings for QuickJS, a modern Javascript interpreter, compiled to WebAssembly.
https://github.com/justjake/quickjs-emscripten

quickjspp - QuickJS wrapper for C++.
https://github.com/ftk/quickjspp

QuickJS-raylib - C Game engine
https://github.com/sntg-p/QuickJS-raylib

qjs-glfw
https://github.com/rsenn/qjs-glfw

quickjs-ffi
https://github.com/shajunxing/quickjs-ffi

quickjs_dart
https://pub.dev/documentation/quickjs_dart/latest/

Quick js flutter
https://flutterawesome.com/a-quickjs-engine-for-flutter/

Quick js android
https://developpaper.com/tutorial-on-using-quickjs-javascript-engine-in-android/

QuickJS-Pascal
https://github.com/Coldzer0/QuickJS-Pascal

WasmEdge - extensible WebAssembly runtime for cloud native, edge, and decentralized applications.
https://github.com/WasmEdge/WasmEdge

quickjs - Go bindings to QuickJS 
https://github.com/lithdew/quickjs

quickjs-rs - A Rust wrapper for QuickJS.
https://github.com/theduke/quickjs-rs

Imgui and QuickJS
https://github.com/KusStar/ABCDEFGui


-----------

## License
MIT



