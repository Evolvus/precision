# Precision 100 Operators
The **Precision100** framework follows an inside out architecture, nearly all components of the framework can be enhanced by using `operator`s. An `operator` can be used to encapsulate commonly repeated activites of a project e.g. *spool* `operator` or it can be used to interface with tools e.g. *sql-plus* `operator`. If you dont find a `operator` that suits your purpose you can always define your own. As with a project the `operator` is well defined by the framework.

The framework supports three kinds of `operator`s. 
1. `operator` which executes work instructions. e.g. *sql-plus* `operator`. 
2. `repo-operator` which serves as an interface to the different repository types. e.g *file-repo-operator* and *git-repo-operator* `repo-operator`s.
3. `connect-operator`s which serves as an inteface with different kinds of connections. e.g. *oracle* `connect-operator` encapulates the connection information needed to connect to a Oracle database

By default the framework ships with the following,
1. *file-repo-operator* (`repo-operator`)
2. *git-repo-operator* (`repo-operator`)
3. *unknown-repo-operator* (`repo-operator`)
4. *shell* (`operator`)
5. *unknown-file-type* (`operator`)

If any other `operator` is needed by the project they must be installed before executing any `iteration`s.

As with **Precision 100** projects, an `operator` is also a file system folder that contains the following,
1. A operator registry file i.e. `operator.reg` in the folder (mandatory).
2. A folder by name `conf` (mandatory).
3. A folder by name `bin` (mandatory).
4. A file by name `operator-template.sh` in the `bin` folder (mandatory).
5. A file by name `.operator.env.sh` in the `conf` folder (optional)
6. A shell file by name `on-install.sh` in the folder (optional)
7. A shell file by name `on-exec.sh` in the folder (optional)
8. A shell file by name `on-init-exec.sh` in the folder (optional)
 

## Operator
An `instruction` can be described as an `operator` along with its parameters. The following list gives the `operators` and the parameters it can take.

| Operator | Instruction Example |
|----------|---------------------|
| [shell](#shell) | *10,abc.sh,sh* |
| [unknown-file-type](#unknown-file-type) | Not invoked directly |
| [sql-plus](#sql-plus) | *10,abc.sql,sql* |
| [loader](#loader) | *10,abc.ctl,loader* |
| [smart-loader](#smart-loader) | *10,table_abc,smart-loader* |
| [spool](#spool) | *10,table_abc,spool* |
| [map-file](#map-file) | *10,casa.tsv,map-file* |
| [smart-map-file](#smart-map-file) | *10,casa.tsv,smart-map-file* |


### Shell
The *shell* `operator` executes a shell script that is located in the `container`. The name of the shell script is passed as a parameter in the `instruction`. It throws an error if the script cannot be found in the `container`.

#### Installation
The *shell* `operator` comes installed with the framework. To install a newer version execute the following
```
./bin/install-operator.sh <path to operator bundle> shell
```
#### Parameters
Name of the script file

#### Dependency
None.

#### Instruction Example
```
10,abc.sh,sh
```
or
```
10,abc.sh,shell
```

---

### unknown-file-type
This `operator` is installed as a part of the framework, it is invoked when the framework is unable to identify the `operator` needed to execute the instruction. This `operator` merely echos the warning to standred output.

#### Installation
The *unknown-file-type* `operator` comes installed with the framework. To install a newer version execute the following
```
./bin/install-operator.sh <path to operator bundle> unknown-file-type
```

#### Parameters
None.

#### Dependency
None.

#### Instruction Example
This `operator` is never used directly. This is internally used by the framework as a fallback for conditions where it is not able to identify which operator to use.

---

## Repo Operator


## Connect Operator

1. [Project definition](#project-definition)
