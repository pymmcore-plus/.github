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
   > the microscope is written in C++. `pymmcore` has long existed as a
   > way to programatically control micro-manager from python.

2. **[pymmcore-plus](https://github.com/pymmcore-plus/pymmcore-plus)**

   The main export of pymmcore-plus is `pymmcore_plus.CMMCorePlus`: a subclass of
   `pymmcore.CMMCore` that provides: 
   - addition convenience functions beyond the standard CMMCore API.
   - a more robust event/callback system for monitoring the state of `CMMCore` and
     reacting to events that occur.
   - a pure-python acquisition engine that enables running standard multidimensional
     experiments *without* requiring a Java runtime running in the background.

3. **[useq-schema](https://github.com/pymmcore-plus/useq-schema)**

   `useq-schema` is an implementation agnostic _schema_ for a sequence
   of events during a multi-dimensional imaging acquisition.  It is essentially
   just a specification for how to _describe_ a microscopy experiment declaratively
   in, for example, a JSON or YAML file, or in python dataclasses.
   
   The `pymmcore_plus.CMMCorePlus.run_mda` method accepts an instance of a
   `useq.MDASequence` object as an input, but conceptually, any microscope control
   system (independent of micro-manager) could implement support for `MDASequence`.

4. **[pymmcore-widgets](https://github.com/pymmcore-plus/pymmcore-widgets)**

   `pymmcore-widgets` is a set of Qt-based widgets, each of which provide GUI-based
   readout and control of certain components controlled by an underlying
   `pymmcore_plus.CMMCorePlus` instance (for example, a shutter widget, a stage
   controller, or a multi-dimensional acquisition builder).
   
   It can be used (perhaps in combination with your own custom widgets) to create
   pure python GUI interfaces for controlling micro-manager.
   
5. **[napari-micromanager](https://github.com/pymmcore-plus/napari-micromanager)**

   `napari-micromanager` is a high-level plugin for [napari](https://github.com/napari/napari).
   It uses all of the packages listed above, and composes widgets from `pymmcore-widgets`
   into a complete GUI capable of running a microscope and showing the collected images
   in a multidimensional viewer.
 
