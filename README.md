# Project Title
UNICA ACQUISTI

Gestione del ciclo passivo

# Notes
The following documentation, and all the documentation present in the project
components adhere to the [RFC-2119]( https://tools.ietf.org/html/rfc2119 )
regarding the requirement level key words.

# Project Description
This is a multi-module project handling the purchasing cycle for the Public
Administration.

The modules are as follow:
- backend services:
  - [cpassbe]( https://github.com/unica-open/unica-acquisti-cpassbe ): REST service
  implementation
  - [cpassrepeng]( https://github.com/unica-open/unica-acquisti-cpassrepeng ):
  Servlet implementation of the Report Engine
- frontend services:
  - [cpassfe]( https://github.com/unica-open/unica-acquisti-cpassfe ): Angular
  application
- transversal:
  - cpassbatch: CLI/batch projects to be invoked by a scheduler (WIP)
  - [cpassdb]( https://github.com/unica-open/unica-acquisti-cpassdb ): database
  implementation, with all the required scripts
  - [cpassmanual]( https://github.com/unica-open/unica-acquisti-cpassmanual ):
  user manual
  - [cpassreptpl]( https://github.com/unica-open/unica-acquisti-cpassreptpl ):
  report templates to be used by the engine
  - cpassscript: CLI scripts to be invoked by a scheduler (WIP)

# Configurations
For the configuration of each single module, please refer to the `README.md`
file which is present in each module.

# Getting Started
Please refer to the Prerequisites section to gather the requested configuration
prior to configure the project.

Please refer to the Installing section for specifications about the
installation process.

# Prerequisites
- The Java projects are written in UTF-8 and are compatible with Java 11.0.6
- Apache Maven 3.6.3 for the building process (the corresponding Maven Wrapper
scripts are present to enable the compilation even without the dependency)
- All the libraries listed in the BOM.csv must be accessible to compile the
project. The libraries are published at [http://repart.csi.it](http://repart.csi.it)
which is set as the Maven repository in the `pom.xml` files
- A "Java EE8 full profile"-compatible Application Server (tested on JBoss
Wildfly 17.0.1)
- The correct version for the DBMS (tested on PostgreSQL 9.6.10)

# Installing
Please refer to the [INSTALLATION.md](./INSTALLATION.md) file for the steps
required for the installation

# Contributing
Please read [CONTRIBUTING.md](./CONTRIBUTING.md) for details on our code of
conduct, and the process for submitting pull requests to us.

# Versioning
We partially use Semantic Versioning for versioning. (http://semver.org) \
A major version increment in SemVer standard corresponds to a non-compatible
upgrade of the project; yet a non-compatible upgrade to the project not
necessarily corresponds to a major version increment.

# Authors
See the list of contributors who participated in this project in file
[AUTHORS.txt](./AUTHORS.txt).

# Copyrights
See the list of copyrighters in this project in file Copyrights.txt\
"&copy; Copyright CSI Piemonte – 2020".

# License
The source code is licensed under the European Union Public Licence 1.2 or
later.\
SPDX-License-Identifier: EUPL-1.2-or-later\
See the [**"EUPL v1_2 IT-LICENSE.txt"**](./EUPL%20v1_2%20IT-LICENSE.txt)
and [**"EUPL v1_2 EN-LICENSE.txt"**](./EUPL%20v1_2%20EN-LICENSE.txt) files for
details.

The documentation is licensed under the Creative Commons Attribution 4.0
International.\
SPDX-License-Identifier: CC-BY-4.0\
See the [**"CC-BY-4.0 EN-LICENSE.txt"**](./CC-BY-4.0%20EN-LICENSE.txt) file for
details.
