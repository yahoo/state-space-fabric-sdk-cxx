# Hyperledger Fabric C++ API for State Space

This repository contains a C++ API for use with [Hyperledger Fabric](https://github.com/hyperledger/fabric).  The implementation herein is optimized to perform with Hyperledger Fabric v1.4.  That is the core dependency of the State Space reference implementation of the IAB PrivacyChain Technology Specification.

The main body of documentation for the State Space reference implementation of the IAB PrivacyChain Technology Specification can be found with the [packaging](https://github.com/yahoo/state-space-packaging]).  The overview and administrative declarations herein are necessarily summary in nature. The declarations and definitions in the packaging area are complete and should be interpreted as superceding these when the two are in conflict.

![banner](logo.png)

This repo supports the State Space reference implementation of the IAB PrivacyChain Technology Specification.

A summary overview is as follows:
* IAB [PrivacyChain](https://github.com/InteractiveAdvertisingBureau/PrivacyChain), contains
    * Specification Documents
    * Runbooks, Operation Documents
    * Project Governance Documents
    * Reference Design
* State Space reference implementation of the IAB PrivacyChain Technology Specification
    * [Packaging](https://github.com/yahoo/state-space-packaging), the packaging, the top-level repository.
    * [Apanolio](https://github.com/yahoo/tunitas-apanolio), a "Northside" API Service, as a macroservice, in [Apache HTTPd](https://httpd.apache.org/).
    * [Montara](https://github.com/yahoo/tunitas-montara), a "Northside" API Service, as a microservice.
    * [Tooling](https://github.com/yahoo/state-space-tooling), some operability tooling.
    * [Testing](https://github.com/yahoo/state-space-testing), some testing and performance assessments.
    * [PrivacyChain C++](https://github.com/yahoo/PrivacyChain-sdk-cxx), part of the "Southside" service components.
    * [Hyperledger Fabric C++](https://github.com/yahoo/hyperledger-fabric-sdk-cxx), part of the "Southside" service components.
* [Hyperledger Fabric](https://github.com/hyperledger/fabric), the upstream.

## Table of Contents

- [Background](#background)
- [Dependencies](#dependencies)
- [Installation](#installation)
- [Configuration](#configuration)
- [Build](#build)
- [Usage](#usage)
- [Security](#security)
- [Contribute](#contribute)
- [Maintainers](#maintainers)
- [License](#license)

## Background

The [Hyperledger Fabric](https://www.hyperledger.org/projects/fabric) project provides a wide range of components to support its feature-rich operations.  This repo contributes a C++ (C++20) client for use with Hyperledger Fabric v1.4..

The client library provided here contains general access capabilites for the Hyperledger Fabric database.  It is expected that this client will be used with the State Space reference implementation of the IAB PrivacyChain Technology Specification.  Further details about that system can be found with the [overview](https://github.com/yahoo/state-space-packaging]) of the State Space project.

## Dependencies

The [configuration](#configuration) step will check for many but not all required packages and operating system features.  There is a list of known [package-dependencies](https://github.com/yahoo/hyperledger-fabric-sdk-c++/blob/master/PACKAGES.md) which you will need to install beyond your base operating system.

Generally, the dependencies are among:
- The Hyperledger Fabric database and its Public Key Infrastructure (PKI) services.
- Various components of the Tunitas system; <em>e.g.</em> the [Basic Components](https://github.com/yahoo/tunitas-basic).
- A modern (C++2a) development environment.
- A recent Fedora, but any recent Linux distro should suffice.

The State Space project was developed on Fedora 27 through Fedora 30 using GCC 7 and GCC 8 with `-fconcepts` and at least `-std=c++1z`.  More details on the development environment and the build system can be found in [temerarious-flagship](https://github.com/yahoo/temerarious-flagship/blob/master/README.md).

## Installation

You may install this repo and its dependents by running the following command:

``` bash
git clone https://github.com/yahoo/hyperledger-fabric-sdk-c++.git
```

This will create a directory called `hyperledger-fabric-sdk-c++` and download the contents of this repo to it.

You may find that your organization or your operating system does not allow punctuation in repository names.  The available resource may therefore be named `hyperledger-fabric-sdk-cxx`.  Use your good judgement.

The expected application for the `hyperledger-fabric-sdk-c++` repo is as a submodule of a larger build of the State Space reference implementation of IAB PrivacyChain Technology Specification.  The configuration, build, and installation intructions herein pertain only to maintenance operations on this repository.  The [configuration](https://github.com/yahoo/state-space-packaging/blob/master/README.md#Configuration) steps for the full project are with the [State Space packaging](https://github.com/yahoo/state-space-packaging).

The customary installation location for Hyperledger Fabric is `/opt/hyperledger/fabric` but you may configure the build to use some other location.

## Configuration

The build system is based upon [GNU Autotools](https://www.gnu.org/software/automake/manual/html_node/index.html).

The configuration of the repo consists of two steps which must be done once.
1. `./buildconf`
2. `./configure`

The first step performs some crude assessments of the build environment and creates the site-specific `configure'. Of course `configure --help` will explain the build options.  The general options to `configure` are widely [documented](https://www.gnu.org/prep/standards/html_node/Configuration.html).

The `buildconf` component is boilerplate and can be updated from [temerarious-flagship](https://github.com/yahoo/temerarious-flagship/blob/master/bc/template.autotools-buildconf) as needed.  The [Tunitas Build System](https://github.com/yahoo/temerarious-flagship) should be available in `/opt/tunitas` and the template at `/opt/tunitas/share/temerarious-flagship/bc/template.autotools-buildconf`

## Build

The simplest configure-compile-install recipe is:

``` bash
./buildconf &&
./configure &&
make all &&
make check &&
make install &&
echo OK DONE
```

## Usage

This package produces libraries (a.k.a. <em>a software development kit</em>).  It must be used with other components to make a complete system.

The [packaging](https://github.com/yahoo/state-space-packaging]) contains more detail on how to build the whole system as well as instructions for packaging and deployment of such a system not bare metal or in containers.

## Security

This project does not have any specific security concerns.  As always, the integrity of the build process is a requirement for the integrity in the deployment and operations phases.

The documentation on the [Security Model](https://hyperledger-fabric.readthedocs.io/en/release-1.4/security_model.html) of Hyperledger Fabric should be consulted prior to deployment. Additional background information on the [Certificate Authority](https://hyperledger-fabric-ca.readthedocs.io/en/release-1.4/) system of Hyperledger Fabric (v1.4) can be found in the general documentation.

As always, before you deploy code into a production-facing environment you should review access and capability grants which have been established for your installation.

Please refer to the overall [Security Notice](https://github.com/yahoo/state-space-packaging/blob/master/README.md#Security) in the [lead repo](https://github.com/yahoo/state-space-packaging) of the State Space Project.

## Contribute

Please refer to [the contributing.md file](Contributing.md) for information about how to get involved. We welcome issues, questions, and pull requests. Pull Requests are welcome.

## Maintainers
- Wendell Baker <wbaker@verizonmedia.com>
- the State Space Team

You may contact us at least at <state-space@verizonmedia.com>

## License

This project is licensed under the terms of the [Apache 2.0](LICENSE-Apache-2.0) open source license. Please refer to [LICENSE](LICENSE) for the full terms.
