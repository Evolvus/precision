# Understanding the Precision 100 Framework

The **Precision 100** framework provides a protocol to declaratively define simple acycle workflow(s) of `instruction`(s) and provides a set of API's to interogate and execute the workflow(s). (A workflow in **Precision 100** parlance is a `dataflow` and we will be using `dataflow` interchangably going forward)

The **Precision 100** API's are consumed by `clients` who use them to provide different interfaces to execute the `dataflow`. Examples of **Precision 100** clients are `precision-native` or `scheduler-native`

## **Precision 100** Project
A **Precision 100** Project represents an ordered set of `dataflow`(s). A **Precision 100** project is a file system folder that contains the following,
1. A folder by the name `dataflows` (mandatory). 
2. A folder by the name `containers` (mandatory).
3. A project registry file named `project.reg` inside the `dataflows` folder (mandatory).
4. The `dataflows` folder can have one or more `dataflow` registry files (optional).
5. The `containers` folder can have one or more folders (optional). A folder located here is referred to as a `container`.
6. Every `container` *if it exists* must have a container registry file named `container.reg` (mandatory).
7. The `container` folder can have one or more files (optional). These files are referred to as `instruction`s.


The `the-empty-project` [example](./the-empty-project.md) gives an illustration of a minimal but valid **Precision 100** project. This project has no `dataflow`s or `container`s and obviously does nothing. A typical **Precision 100** project can have one to ten `dataflow`s and maybe one to fifty `container`s. The framework does not place any limit on the number of `dataflow`s or `container`s that can be contained in a project.

## Dataflows
A `dataflow` is a high level construct of the **Precision 100** framework. It defines a workflow of `instruction`s that can be executed. How a `dataflow` is triggered depends on the `client` being used. e.g. The `precision-native` client displays each `dataflow` in a project as a menu option. Choosing the menu option executes the corresponding `dataflow`. Other `clients` may have a different mechanism. 

A **Precision 100** `dataflow` describes the `dataflow` using registry files and `container`s. In that sense a `dataflow` is defined as an ordered set of `container`s. The `dataflow` registry file contains the ordererd list of `container`(s). This file is interogated by the framework's API's to gather the `container`(s) that need to be executed.

