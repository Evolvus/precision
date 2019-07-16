# Precision 100 Migration Framework
**Precision 100** provides a framework to execute simple acyclic workflow of `instruction`s. An `instruction` can be anything from a `shell` script to a `sql` file and anything in between. 

## Quick Usage
```
git clone --recurse-submodules git@github.com:ennovatenow/precision-native.git

cd precision-native
./configure-project.sh
./init-exec.sh mock1
./migrate.sh
```

This uses the `precision-native` client to execute the simple-demo project.

```
The --recurse-submodules parameter is required while cloning because we have a dependency with Precision100 framework.
```
## Operating System Requirements
Precision 100 Framework uses the `bash` shell for most of its work, more specifically it uses bash 4.2 features like associative arrays. Although all development and tests of the framework is done on `linux`, the framwork should run on any operating system supporting the `bash` shell.
Make sure you check your `bash` version.

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
As mentioned above, the only requirement for the framework is the `bash` shell of the correct version. However, the framework allows you to install operators. These operators can have different requirements. You will need to read the README for the operators to get the specific details. e.g. The sql-plus operator will require that Oracle client be instlled or the git repo operator would need `git` client to be installed annd configured properly.


The `instruction`s are executed by `operators`. `operators` map the `instruction`s to appropriate utilities which can execute them. e.g. a `sql` `instruction` will be executed by `sqlplus` utility. `instrcution`s are grouped into `containers` and `containers` are grouped into `dataflows`.

A **Precision 100** `project` is a set `dataflows`. Develepors build the `instructions`, `containers` and `dataflows` and then release it into `repositories`. The framework connects to the `repositories` and executes the `project`

The framework specifies the following,
1. [Project definition](#project-definition)
2. Repository definition
3. Operator framework

`repositories` and `projects` allow well-tested workflows and best practices to be shared and monetised. `Project` designers can focus on building proper workflows embedding best practics and once the workflows have stabalized the same can be published to a `repository` to share

The framework also brings the familiar development flow to work flow definitions. The `project` changes are made by developers and released to the repository. The framework extracts the same, branches it if possible and executes it.

## Project Definition
A Precision100 `project` is defined as an ordered set of `dataflows`.
A Precision100 `dataflow` is defined as an ordered set of `pipelines`.
A Precision100 `pipeline` is defined as an ordered set of `containers`.
A Precision100 `container` is a defined as an ordered set of work instructions. 

Projects can be created using a designer tool, but more often than not they are just copied from existing projects or templates. Once a project has been designed they are published to `repositories`.

e.g. A Environment Provisioning Project could look as follows. Developers make changes to the files, check-in the changes and do a release. The Framework can use the released branch to download the project and execute it.

| Dataflow | Pipeline | Container | File |
|----------|----------|-----------|------|
| Create Environment | Create Module 1 Environment | Create Tables | create_object.sql |
|   |   | Create SP | create_sp.sql |
| Load Data | Load Master Data | Load Generic Master Data | insert-master-data.sql |
|   |   | Load Specfic Master Data | load-demo-master-data.sql |
|   | Load Other Data | Load Other Data | load-demo-data.sql |
| Verify Environment | Verify Environment | Verify Environment | volume-profile.sql |
|   |   |   | verify-environment.sql |

## Repositories
A `repository` is a store of published `projects`. The framework connects to the `repository` to download and execute `projects`. The framework supports repositories of type GIT and FILE. If the `repository` supports branching, branch is created for each execution of the `project`. The framework connects to repositories using pluggable `repo-operators`. By default the framework ships with support for the 'FILE' and 'GIT' repositories.


## Operator framework
The Precision100 framework follows an inside out architecture, nearly all components of the framework can be enhanced by using `operators`. The framework supports three kinds of `operators`. An `operator` which serves an interface for the work instructions to be executed. e.g. `sql-plus` operator, A `repo-operator` which serves as an interface to the different `repository` types and `connect-operators` which is used to interfac with different data sources and targets.


### A longer example
To-do


## Contributing
Thank you very much for considering to contribute!

Please make sure you follow our [Code Of Conduct](CODE_OF_CONDUCT.md) and we also strongly recommend reading our [Contributing Guide](CONTRIBUTING.md).
