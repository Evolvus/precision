# Load and Spool Example
In this example, We will create a project to Create a table in a staging area, Load data into it  and then spool the data into a file. To achieve these tasks we will use the *sql-plus*, *loader* and the *spool* operator and learn about them. We will also learn a little about how **Precision 100** makes use of environment variables and also a little about `precision-native` client. 

We will use Github as a repository for this project.

## Prerequisities
To create and execute the project you need to have the following,

1. A [Github](https://www.github.com) account
2. Git client installed on your machine.
3. A running *Oracle* database with a schema named *precision100*
4. A working *sql plus* client
5. A working *sql loader* client

You can find many tutorials and videos to install Git on your operating system. e.g. you can look at [this one from Atlassian](https://www.atlassian.com/git/tutorials/install-git) or [this from the Git book](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

Installing and confguring a Oracle database is beyond the scope of this tutorial. If you already have one, we can use it else the recommended way is to install [docker](https://docs.docker.com) for your operating system (You can find several tutorials to assist you with it. e.g. [here](https://docs.docker.com/)) and run a Oracle docker image. Articles like [these](https://sqlmaria.com/2017/04/27/oracle-database-12c-now-available-on-docker/) can help with it.

Next, you need to install *sqlplus* and *sqlldr*. These are Oracle client tools. You can learn more about them [here](https://www.oracle.com/technetwork/database/database-technologies/instant-client/overview/index.html). Specifically you need to install the the *base*, *sqlplus* and *tools* packages for your operating system.

You will also need to make *tns* entries to ensure that the *sqlplus* and *sqlldr* is able to connect to the Oracle database. After all the setup the following should connect to your database, if it is then we are ready to move to the next steps.

```
sqlplus precision100/yourprecisionpassword@sid
```

## Designing the Project
The goal of this example is to load data into a table and extract its contents onto a CSV file. Let us see the different ways we can do this.

We can have a single container where we can put the `instruction`s to create the table in the staging area, load it and then extract its contents into a file. We can then wrap the container in a `dataflow`. The `dataflow` is exposed to the `precision-native` client and on choosing this option it will execute all the `instruction`s at once. That is one way to do it, 3 `instruction`s, 1 `container` and 1 `dataflow`.

Lets look a another way to do the same thing, we can have three containers namely *setup*, *load* and *spool*. The *setup* `container` has the `instruction` to create the table in the staging area, the *load* `container` has the `instruction` to load the data into the table and finally the *spool* `container` has the `instruction` to generate the CSV file of the contents of the table. We can organize these `container`s in multiple ways. We have one `dataflow` to wrap all the three containers, in this case once the `dataflow` is exposed to `precision-native` we have one single menu option and all the `instruction`s are executed at once. Another way is to have 3 `dataflow`s, say named *setup*, *load* and *spool*. Each wrapping the eponymous `container`, when exposed in `precision-native` we would have 3 menu options.

There is no right or wrong way to organize your `instruction`s. It depends on how the project is going to be used. e.g. If this were a task which does not require any human intervention then having 1 `dataflow` with one `contianer` would suffice, and in all probablility we would be using `schedular-native` or some such `client`. On the other hand, like in this example we want to stop at every stage and check the results, it is good to distribute the `instruction`s across `container`s and `dataflow`s and execute them one by one.

In production the biggest factor in organizing your project is validating the result of each step. When you are loading data or performing complex validations it is a best practice to validate the results of each step before moving to the next. e.g. If you are loading a million records you want to make sure that the loading process actually loaded each of the records and if needed make corrections and rerun the load, before moving on the next steps. This would decide how the `dataflow`s and `container`s are organized.

For our example, we will design the project as follows,

| Dataflow | Container | Description |
|----------|-----------|-------------|
| Setup | setup | Drop and Create the table |
| Load | load | Truncate the table and load data into it |
| Spool | spool | Generate the CSV file |
