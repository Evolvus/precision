# Understanding the Precision 100 Framework

The **Precision 100** framework provides a protocol to declaratively define simple acycle workflow(s) of `instruction`(s) and provides a set of API's to interogate and execute the workflow(s). (A workflow in **Precision 100** parlance is a `dataflow` and we will be using `dataflow` interchangably going forward)

The **Precision 100** API's are consumed by `clients` who use them to provide different interfaces to execute the `dataflow`. Examples of **Precision 100** clients are `precision-native` or `scheduler-native`

## **Precision 100** Project
A **Precision 100** Project represents an ordered set of `dataflow`(s). A **Precision 100** project is a file system folder that contains the following,
1. A folder by the name `dataflows`. (mandatory) 
2. A folder by the name `containers`. (mandatory)
3. A project registry file named `project.reg` inside the `dataflows` folder. (mandatory)
4. The `dataflows` folder can have one or more `dataflow` registry files. (optional)
5. The `containers` folder can have one or more folders. (optional)
6. The folder inside the `containers` folder *if it exists* must have a container registry file named `container.reg`. (mandatory)


