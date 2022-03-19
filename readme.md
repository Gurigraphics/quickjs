# QuickJS

QuickJS is a small and embeddable Javascript engine written in C89. Binary file is only about 1Mb.
It was created by Charlie Gordon and Fabrice Bellard creator of FFMPEG and QEMU.
It supports the ES2020 specification including modules, asynchronous generators, proxies and BigInt.
It optionally supports mathematical extensions such as big decimal floating point numbers (BigDecimal), big binary floating point numbers (BigFloat) and operator overloading.

Official site: https://bellard.org/quickjs/

The main documentation is in doc/quickjs.pdf or doc/quickjs.html.

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

### How Build:

##### 1. Download and install MSYS2 in C:\msys64
"msys2-x86_64-20220128.exe"
https://www.msys2.org/

##### 2. Run msys2.exe

##### 3. Install mingw
Execute in msys:
```sh
pacman -Syu
pacman -Su
pacman -S --needed base-devel mingw-w64-x86_64-toolchain
pacman -S mingw-w64-x86_64-gcc mingw-w64-x86_64-make mingw-w64-x86_64-dlfcn
echo "#! /bin/sh" > /mingw64/bin/make
echo "\"mingw32-make\" \"\$@\"" >> /mingw64/bin/make
```

##### 4. Add to variable PATH
```sh
C:\msys64\mingw64\bin
C:\msys64\usr\bin
```

##### 5. Clone this repository
```sh
git clone https://github.com/Gurigraphics/quickjs.git
```

##### 6. Build: Run in CMD
```sh
cd quickjs
make LDEXPORT="-static -s"
```
Files: qjs.exe | qjsc.exe | run-test262.exe
 
 -----------

### Hello World Binary File

Create file: **hello.js**  
```js
console.log( "Hello world" )
```

Compile file: **hello.js** to: **hello.c**
```sh
qjsc -e -o hello.c hello.js
```

Compile file: **hello.c** to **hello.exe**
```sh
gcc -D_GNU_SOURCE -I./ -o hello hello.c -static -s -L./ -lquickjs -lm -ldl -lpthread 
```

### How Run a Module File

Create file: **data.js**  
```js
export const hello = "Hello World";
```

Create file: **example.js**  
```js
import { hello } from "data.js"
console.log( hello )
```

Execute 
```sh
qjs -m example.js
```

 -----------

### Outher Examples

Edit file: **example.js**  
```js
import * as std from "std";
import * as os from "os";

var func = (value) => {
   std.printf(os.platform) // win32
}
func("name")
```
Execute 
```sh
qjs -m example.js
```

-----------

### Create a C Module Example
Create file: **my_module.js**
```js
import * as myModule from 'my_module'

const value = myModule.plus(1, 2)
console.log("Result:", value)

// Output => Result: 3
```

Create file: **my_module.c**
```c
#include "quickjs.h"
#include "cutils.h"

static JSValue plusNumbers(JSContext *ctx, JSValueConst this_val, int argc, JSValueConst *argv)
{
    int a, b;

    if (JS_ToInt32(ctx, &a, argv[0]))
        return JS_EXCEPTION;
    
    if (JS_ToInt32(ctx, &b, argv[1]))
        return JS_EXCEPTION;
        
    return JS_NewInt32(ctx, a + b);
}

static const JSCFunctionListEntry js_my_module_funcs[] = {
    JS_CFUNC_DEF("plus", 2, plusNumbers),
};

static int js_my_module_init(JSContext *ctx, JSModuleDef *m)
{
    return JS_SetModuleExportList(ctx, m, js_my_module_funcs, countof(js_my_module_funcs));
}

JSModuleDef *js_init_module_my_module(JSContext *ctx, const char *module_name)
{
    JSModuleDef *m;
    m = JS_NewCModule(ctx, module_name, js_my_module_init);
    
    if (!m)
        return NULL;
    
    JS_AddModuleExportList(ctx, m, js_my_module_funcs, countof(js_my_module_funcs));
    return m;
}
```

Generate file: **my_module.o**
```sh
gcc -c my_module.c
```

Add to "lib objects list" in Makefile 
```sh
QJS_LIB_OBJS= ... $(OBJDIR)/my_module.o
```

Add **my_module** to file **qjsc.c**. After "std" and "os" modules
```sh
/* add system modules */
namelist_add(&cmodule_list, "std", "std", 0);
namelist_add(&cmodule_list, "os", "os", 0);
// our module
namelist_add(&cmodule_list, "my_module", "my_module", 0);
```

Generate a new compiler **qjsc.exe**
```sh
make qjsc LDEXPORT="-static -s"
```
 
Generate file: **my_module_js.c**
```sh
qjsc -e -m -o my_module_js.c my_module.js 
```

Generate file: **my_module.exe**
```sh
gcc -D_GNU_SOURCE -I./ -o my_module my_module_js.c -static -s -L./ -lquickjs -lm -ldl -lpthread
```



### References
| File |  Repository |
| ------ | ------ |
| Makefile - Windows 64bits | https://github.com/mengmo/QuickJS-Windows-Build |
| Writing native modules in C for QuickJS engine | https://calbertts.medium.com/writing-native-modules-in-c-for-quickjs-engine-49043587f2e2 |


-----------

## License
MIT



