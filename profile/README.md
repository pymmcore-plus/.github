# pymmcore-plus

This github org contains a number of packages that work together (and in 
conjunction with [pymmcore](https://github.com/micro-manager/pymmcore))
to control microscopes in a pure python/C environment (i.e. with no
Java dependency)

1. **[pymmcore](https://github.com/micro-manager/pymmcore)** *(not in this org)*

   `pymmcore` is a [SWIG](https://www.swig.org/) around the C++ code at the core
   of micro-manager ([mmCoreAndDevices](https://github.com/micro-manager/mmCoreAndDevices))
   
   > **side-note**: there is a common misconception that micro-manager is written in Java.
   >
   > The *GUI* of micro-manager is written in java, but the code that actually controls
   > the microscope is written in C++. `pymmcore` has also long existed as a
   > way to programatically control micro-manager from python.

2. ...
