# Precision 100 Framework
**Precision 100** provides a framework to execute simple acyclic workflow of `instruction`s. An `instruction` can be anything from a *shell* script to a *sql* file and anything in between. 

## Quick Usage
```
git clone --recurse-submodules https://github.com/ennovatenow/precision-native.git precision-native

cd precision-native
./configure-project.sh "GIT" "https://github.com/ennovatenow/the-empty-project.git" "The Empty Project"
./init-exec.sh mock1
./migrate.sh

./close-exec.sh mock1
```

This uses the *precision-native* client to execute the *the-empty-project* project.

```
The --recurse-submodules parameter is required while cloning because we have a dependency with Precision100 framework.
```

## What next?
The best way forward is to look at [the-longer-example](./the-longer-example.md) and other [examples](./examples.md) and go through it. Alternatively you can go through the [concepts](./concepts.md) and then the [examples](./examples.md)


## Operating System Requirements
**Precision 100** Framework uses the *bash* shell for most of its work, more specifically it uses *bash* 4.2 features like associative arrays. Although all development and tests of the framework is done on *linux*, the framwork should run on any operating system supporting the *bash* shell.
Make sure you check your *bash* version.

```
$ bash --version
GNU bash, version 4.4.19(1)-release (x86_64-pc-linux-gnu)
Copyright (C) 2016 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>

This is free software; you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
```

## Hardware requirements
The hardware requirements of Precision 100 Framework depend on the volume of data to be moved and the window within which it needs to be done.You can run the framework on a `linux` laptop with 4 cores and 4 gigs of RAM for a simple demo. 

## Software Prerequisites
As mentioned above, the only requirement for the framework is the *bash* shell of the correct version. However, the framework allows you to install `operator`s. These `operator`s can have different requirements. You will need to read the README for the operators to get the specific details. e.g. The *sql-plus* `operator` will require that Oracle client be instlled or the *secure-oracle* `connect-operator` would need *openssl* to be installed and configured properly.

```
*spool* operator for example uses 'set markup on csv' to generate spool files. This feature was introduced in *sql-plus* version 12.2. 
```
