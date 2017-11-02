# CLARUS Tools

This metapackage serves as a compilation of required repositories to compile
and package the CLARUS Tool suite:

* Security Policy Manager (SecPolMgmt)
* Access Rights Manager (ARM)
* Security Administration (SecAdm)

It also contains the configuration files, execution scripts that are part of
the distribution packages. Also, this metapackage contains a maven profile that
aids the creation of the distribution packages, including the configuration
files and the invoking scripts.

The aforementioned tools depend on two other repositories that are available
on the CLARUS GitHub site.

In particular, this project serves as a central point to compile and pack the
CLARUS Tools in a single location.

Please note that this package is not required if a single tools needs to be
compiled. Please refer to the README file of the desired tool to obtain more
information about how to obtain the code and how to compile it.

## Requisites

As stated before, this package introduces the dependencies of all the packages
required by the  CLARUS Tools. Before cloning this repository, it is encouraged
to clone the repositories on which this packages depends *__in the same directory__*:

* CLARUS Security Policy Model
`git clone https://github.com/clarus-proxy/security-policy-model.git`

* CLARUS User Library.
This example uses the not-recommended sample user Library. This requirement can
be replaced with the concrte CLARUS User Library once it becomes available
`git clone https://github.com/clarus-proxy/sample-userlibrary.git`

* CLARUS Security Policy Manager
`git clone https://github.com/clarus-proxy/security-policy-mgmt.git`

* CLARUS Access Rights Manager
`git clone https://github.com/clarus-proxy/ARM.git`

* CLARUS Security Administration
`git clone https://github.com/clarus-proxy/security-administration.git`

## Getting the CLARUS Tools metapackage

Once the required repositories have been cloned, it is possible to clone this
repository locally.  It is hardly recommended to clone this repository *__in the
same directory where the requirements reside__*:

`git clone https://github.com/clarus-proxy/clarus-tools.git`

After cloning all the repositories (requirements and this one), the folder structure
should look like this:

`$ tree -L 1.
├── ARM
├── clarus-tools
├── sample-userlibrary
├── security-administration
├── security-policy-mgmt
└── security-policy-model`

## Compiling the tools

The compilation of all the tools is done by using Maven. This software will compute
the right compialtion order and compile then recursively. To do this, simply invoke
maven in the CLARUS Tools folder:

`$ cd clarus-tools #Execute this to move to the clarus-tools folder`

`$ mvn install`

This command will compile the code and provide a local installation of the tools
under the *install* folder

```$ tree -L 2
.
├── README.md
├── eclipse-formatter-config.xml
├── install
│   ├── clarus-adm
│   ├── clarus-arm
│   ├── clarus-mgmt-tools.conf
│   ├── clarus-spm
│   ├── clarus-tools.conf
│   ├── clarus-tools_1.0.2.deb
│   └── libs
├── pom.xml
└── src
    └── main```

## Packaging the tools

This repository contains a scripts to generate a *deb* package to distribute the tools.
To generate this it is required to install the software locally and then call maven
with the *deb-packaging* profile:

`$ mvn install #Created local installation`

`$ mvn install -Pdeb-packaging`

The last command will use the previous installation to create the Debian package under the
*install* folder:

```$ tree -L 2
.
├── README.md
├── eclipse-formatter-config.xml
├── install
│   ├── clarus-adm
│   ├── clarus-arm
│   ├── clarus-mgmt-tools.conf
│   ├── clarus-spm
│   ├── clarus-tools.conf
│   ├── clarus-tools_1.0.2.deb
│   └── libs
├── pom.xml
└── src
    └── main```