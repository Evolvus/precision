# Precision 100 Operators
The **Precision100** framework follows an inside out architecture, nearly all components of the framework can be enhanced by using `operator`s.

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

## Operator
An `instruction` can be described as an `operator` along with its parameters. The following list gives the `operators` and the parameters it can take.

1. [shell](#shell) operator
2. 

### Shell
The *shell* `operator` executes a shell script that is located in the `container`. The name of the shell script is passed as a parameter in the `instruction`. It throws an error if the script cannot be found in the `container`.
###
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
## Repo Operator


## Connect Operator

1. [Project definition](#project-definition)
