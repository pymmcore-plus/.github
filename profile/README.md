# pymmcore-plus

This organization contains a number of packages that work together (in conjunction with [pymmcore](https://github.com/micro-manager/pymmcore))
to control microscopes in a _pure_ python/C environment (i.e. with no Java dependency or cross-process runtime).

The diagram below attempts to clarify how many libraries and components that have been built around the micro-manager ecosystem relate to each other.  The repositories for the components in blue are in this organization ([pymmcore-plus](https://github.com/pymmcore-plus/pymmcore-plus), [useq-schema](https://github.com/pymmcore-plus/useq-schema), [pymmcore-widgets](https://github.com/pymmcore-plus/pymmcore-widgets), [napari-micromanager](https://github.com/pymmcore-plus/napari-micromanager)), everything is else is not (links are provided).

![mm diagram](https://user-images.githubusercontent.com/1609449/202301602-00ba0fd8-df4f-4993-b0ad-8e3d1cefaf42.png)

### In this github org:
- **[pymmcore-plus](https://github.com/pymmcore-plus/pymmcore-plus)** - a drop in super-set of `pymmcore.CMMCore`. Adds a pure-python acquisition engine (analogous to AcqEngineJ, but less developed at the moment); a more robust event/signaling system for monitoring the state of `MMCore`; additional convenience functions and structures; and an improved python developer experience (typing, docstrings, etc...)
- **[useq-schema](https://github.com/pymmcore-plus/useq-schema)** - an implementation agnostic schema for a sequence of events during a multi-dimensional imaging acquisition.  Written in python, but language agnostic and exported as [JSONschema](https://json-schema.org/). It is essentially just a specification for how to describe a microscopy experiment declaratively in, for example, a JSON or YAML file, or in python dataclasses. The `pymmcore_plus.CMMCorePlus.run_mda` method accepts an instance of a `useq.MDASequence` object as an input, but conceptually, any microscope control system (independent of micro-manager) could implement support for `MDASequence`.
- **[pymmcore-widgets](https://github.com/pymmcore-plus/pymmcore-widgets)** -  a set of Qt-based widgets, each of which provide GUI-based readout and control of certain components controlled by an underlying `pymmcore_plus.CMMCorePlus` instance (for example, a shutter widget, a stage controller, or a multi-dimensional acquisition builder).
- **[napari-micromanager](https://github.com/pymmcore-plus/napari-micromanager)** - a high-level plugin for [napari](https://github.com/napari/napari). It uses all of the packages listed above, and composes widgets from `pymmcore-widgets` into a complete GUI capable of running a microscope and showing the collected images in a multidimensional viewer.

### In other orgs:
- **[MMCore (and devices)](https://github.com/micro-manager/mmCoreAndDevices)** - C++ core of micro-manager.  This is what actually communicates with microscope devices.
- **[pymmcore](https://github.com/micro-manager/pymmcore)** - thin python wrapper around [mmCoreAndDevices](https://github.com/micro-manager/mmCoreAndDevices)
- **[napari](https://github.com/napari/napari)** - multidimensional data viewer in Python.
- **[Pycro-manager](https://github.com/micro-manager/pycro-manager)** - python library that controls the Java micro-manager application via inter-process communication.
- **[PycroManagerJava](https://github.com/micro-manager/pycro-manager)** - the Java half of Pycro-manager: a ZMQ server that communicates with the Python client as well as mmstudio and the Java-based acquisition engine
- **[MMStudio](https://github.com/micro-manager/micro-manager)** - the Java-based micro-manager GUI application.
- **[clojure acqEngine](https://github.com/micro-manager/micro-manager/tree/main/acqEngine/src/main/clj/org/micromanager)** - original acquisition engine (written in clojure): this is the bit that has conventionally driven the microscope during an MDA acquisition.
- **[AcqEngJ](https://github.com/micro-manager/AcqEngJ)** - A Java-based alternative engine to the clojure one, originally written for [MicroMagellan]([url](https://micro-manager.org/MicroMagellan)) and Pycro-manager, but being integrated into core micro-manager.
- **MMCoreJ** - The Java component that communicates with the C++ core.

