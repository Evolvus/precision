# Using the *map-file* `operator`
This example will extend the [load and spool example](./load-and-spool-example.md) and illustrate the use of the *map-file* `operator`. The *map-file* `operator` transforms data from source to destination. It uses a *map-file* to describe the mapping between the source and the destination. 

Lets define the problem. The target system expects the following,
1. Data should provided in a CSV format file
2. The CSV file should have the following attributes - Name, Gender, DOB, State, Address 1, Address 2, Old Reference Number, Load Date, Record Flag
3. Name should be in upper case and have a maximum length of 50 characters. Mandatory
4. Gender should be 1 for Male and 2 for Female. Maximum length of 1 character. Mandatory
5. DOB should be in 'yyyy-mm-dd' format. Maximum length 10 characters. Mandatory
6. State should be full name in upper case i.e OHIO for OH. Maximum length 50 characters. Mandatory
7. Address 1. Maximum length 50 characters. Optional
8. Address 2. Maximum length 50 characters. Optional
9. Old Reference Number should be the reference number of the old records. Maximum length 50 characters. Optional
10. Load Date. Should be in 'yyyy-mm-dd' format. Maximum length 10 characters. Mandatory
11. Record Flag. Should be 'NEW' for all records. Maximum length 50 characters. Mandatory

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
The example requires that a we load data into a table, transform it to the requirements of the target system and generate a CSV file in the presecribed format. In that sense the project is very similar to the [load-and-spool-example](./load-and-spool-example.md) but with an extra step to transform the data. We will design the project as follows,


| Dataflow | Container | Description |
|----------|-----------|-------------|
| Setup | setup | Drop and Create the table |
| Load | load | Truncate the table and load data into it |
| Transform | transform | Transform the source to the target format |
| Spool | spool | Generate the CSV file |

## Creating the project
In most of our exa
