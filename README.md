# ams-build
Utilities for testing and buliding of the [AMS - Advanced Module System](https://github.com/kulhanek/ams) package.

## AMS Features:
* software management (sites and modules)
* ams-personal
* integration with [ABS - Advanced Batch System](https://github.com/kulhanek/abs)

## Testing Mode
The typical procedure is:
```bash
$ git clone --recursive https://github.com/kulhanek/ams-build.git
$ cd ams-build
$ ./build-utils/00.init-links.sh
$ ./01.pull-code.sh
$ ./04.build-inline.sh   # build the code inline in src/
```
## Production Build
The typical procedure is:
```bash
$ git clone --recursive https://github.com/kulhanek/ams-build.git
$ cd ams-build
$ ./build-utils/00.init-links.sh
$ ./01.pull-code.sh
$ ./10.build-final.sh
```


