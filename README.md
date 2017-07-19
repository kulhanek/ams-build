# ams-build
Utilities for testing and building of the [AMS - Advanced Module System](https://github.com/kulhanek/ams) package.

## AMS Features:
* software management (sites and modules)
* synchronization of package repositories
* ams-personal
* integration with [ABS - Advanced Batch System](https://github.com/kulhanek/abs)

## Testing Mode
```bash
$ git clone --recursive https://github.com/kulhanek/ams-build.git
$ cd ams-build
$ ./build-utils/00.init-links.sh
$ ./01.pull-code.sh
$ ./04.build-inline.sh   # build the code inline in src/
```

## Production Build
```bash
$ git clone --recursive https://github.com/kulhanek/ams-build.git
$ cd ams-build
$ ./build-utils/00.init-links.sh
$ ./01.pull-code.sh
$ ./10.build-final.sh
```


