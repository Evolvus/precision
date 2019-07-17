# The Longer Example
In this example we will start by creating a simple project that executes two shell scripts. We will not be using any design tool but rather build the entire project from scratch and execute it using **Precision100**. We will be using [Github](https://github.com) as a `repository` for this project. If you don't have an account there, you should get it before going any further. We will calling our project rather unimaginatively "the longer example", with that lets get started.

## Creating the Project.
Create a new repository with the name "the-longer-example" with the description "A sample project to understand the workings of Precision 100". Now execute the following commands.
```
git clone https://github.com/ennovatenow/the-longer-example.git the-longer-example
cd the-longer-example
mkdir dataflows
mkdir containers
touch dataflows/project.reg
touch containers/container.reg
touch containers/container.reg
git add .
git commit -m "created the template"
git push origin master
```
