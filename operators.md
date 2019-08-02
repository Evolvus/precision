# Precision 100 Operators
The **Precision100** framework follows an inside out architecture, nearly all components of the framework can be enhanced by using `operator`s. The framework supports three kinds of `operator`s. 

1. `operator` which executes work instructions. e.g. *sql-plus* `operator`. 
2. `repo-operator` which serves as an interface to the different repository types. e.g *FILE* and *GIT* `repo-operator`s
3. `connect-operator`s which serves as an inteface with different kinds of connections. e.g. *oracle* `connect-operator` encapulates the connection information needed to connect to a Oracle database



1. [Project definition](#project-definition)
