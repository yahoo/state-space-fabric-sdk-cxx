# Required Packages

This document contains an estimate of the tools, components their versions which you will need to build this repository.  More details can be found upstream the documentation for the lead repository, the [State Space Packaging](https://github.com/yahoo/state-space-packaging/blob/master/PACKAGES.md) as well as the [Temerarious Flagship Build System](https://github.com/yahoo/temerarious-flagship/blob/master/README.md).  The mentions in this document pertain only to this repository, the _Hyperledger Fabric C++ SDK_.

## State Space

The [hyperledger-fabric-sdk-c++](https://github.com/yahoo/hyperledger-fabric-sdk-c++) package is the earliest package in the dependency ordering among the State Space packages.  It depends directly upon Hyperledger Fabric, the compiler toolchain and the base operating system.

The lead repository for the State Space suite of services is [state-space-packaging](https://github.com/yahoo/state-space-packaging).

## Hyperledger Fabric

To set up the developmente environment for Hyperledger Fabric, you should refer to the [development environment instructions](https://hyperledger-fabric.readthedocs.io/en/release-1.4/dev-setup/devenv.html).

The dependencies documented therein are at least:
* Git
* Go  (Language)
* Docker
* Docker Compose
* LevelDB or CouchDB

You will need to acquire Hyperledger Fabric from among
* Pull the Docker images from the public repositories using the published instructions, such as [these](https://hyperledger-fabric.readthedocs.io/en/release-1.4/getting_started.html) or [these](https://openblockchain.readthedocs.io/en/latest/Setup/Network-setup).
* Install Hyperledger Fabric from pre-packaged repositories; see the [Availabilities](#availabilities) section below.
* Build from source so you control your software supply chain.

## Tunitas

* [tunitas-basics](https://github.com/yahoo/tunitas-basics) >= 1.8.0, common components of the Tunitas projects.
* [temerarious-flagship](https://github.com/yahoo/temerarious-flagship) >= 1.0.0, some build system components.

The lead repository for the Tunitas suite of services is [tunitas-packaging](https://github.com/yahoo/tunitas-packaging).

## Development Tooling

This is a C++ project.  The project approaches the upcoming C++20 standard, where available.

### C++ 2a Compiler
* `gcc-c++` >= 7.2, feasible.
* `gcc-c++` >= 8.2, current.
* `gcc-c++` >= 9.0, preferred.
* gcc-c++ with [C++ Modules TS](https://gcc.gnu.org/wiki/cxx-modules).

### Build Support
* The [GNU Autotools](https://www.gnu.org/software/automake/manual/html_node/index.html#Top)
    * `automake` >= 1.16
    * `autoconf` >= 2.69
    * `libtool` >= 2.4
    * `make` >= 4.2
* The Tunitas Build System
    * [temerarious-flagship](https://github.com/yahoo/temerarious-flagship) >= 1.0.0, some build system components
* The [S.C.O.L.D.](https://www.scold-lang.org) [toolchain](https://git.scold-lang.org/core) and modules
    * [hypogeal-twilight](https://git.scold-lang.org/core/hypogeal-twilight) >= 0.43, fundamental build system components.
    * [incendiary-sophist](https://git.scold-lang.org/core/incendiary-sophist) >= 0.1, the test harness, is optional.
    * [anguish-answer](https://git.scold-lang.org/core/anguish-answer) >= 0.1, the preprocessor towards a [unitary build](https://mesonbuild.com/Unity-builds.html).
* `perl` prefer `perl` >= 5.28
    * and various perl modules, surely.

##  Components

This section enumerates is a best-estimate abstraction of the component dependencies for [Hyperledger Fabric SDK C++](https://github.com/yahoo/hyperledger-fabric-sdk-c++).  A master list of dependencies for the State Space reference implementation of the IAB PrivacyChain Technology Specification is with the [packaging](https://github.com/yahoo/state-space-packaging/blob/master/PACKAGES.md).

These packages are available via `dnf` or `yum`, if your machine is configured appropriately.

* `gcc-c++` >= 8.2.1
* `cppunit-devel` >= 1.14.0
* `jsoncpp-devel` >= 1.8.4

Modules: [json](https://git.scold-lang.org/modules/json), [nonstd](https://git.scold-lang.org/modules/nonstd), [posix](https://git.scold-lang.org/modules/posix), [std](https://git.scold-lang.org/modules/std), [string](https://git.scold-lang.org/modules/string), [sys](https://git.scold-lang.org/modules/sys); [cppunit](https://git.scold-lang.org/modules/cppunit), [rigging](https://git.scold-lang.org/modules/rigging).

## Operating System

Development commenced on Fedora 27 and has continues on Fedora 30.

A recent Ubuntu should be fine.

## Availabilities

* [Fedora](https://getfedora.com)
    * Fedora 27, possible.
    * Fedora 28, available.
    * Fedora 29, current.
    * Fedora 30, current.
* Hyperledger Fabric
    * <em>Release 01 (Heavy Fish)</em> use Docker (Hyperledger Fabric v1.1) supported Privacy Chain v1.0 <em>Release 01 (Worthy Cupboard)</em>
    * <em>Release 02 (Giddy Llama)</em> unavailable (Hyperledger Fabric v1.2)
    * <em>Release 03 (Furious Eagle)</em> unavailable (Hyperledger Fabric v1.3)
    * <em>Release 04 (Bitter Vole)</em> contains <em>e.g.</em> `hyperledger-fabric-cluster-1.4.0-4.vzmf04.fc27.src.rpm`
* [Tunitas](https://github.com/yahoo/tunitas-packaging/blob/master/README.md)
    * <em>Release 01 (Famous Oak)</em>, current.
    * <em>Release 02 (Towering Redwood)</em>, forthcoming, date TBD.
* [S.C.O.L.D. C++](https://www.scold-lang.org) (Scalable Object Location Disaggregation)
    * <em>Release 02, (Maroon Iron Crow)</em>, possible.
    * <em>Release 03, (Red Mercury Goose)</em>, current
    * <em>Release 04, (Green Copper Heron)</em>, preferred.
