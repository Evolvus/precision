# The Empty Project
This example creates a empty but valid **Precision 100** project. This project can be successfully interrogated by a **Precision 100** client without any errors. This example describes the project the layout and the minimal files required to make the project a valid **Precision 100** project.

## Prerequisities
To create and execute the project you need to have the following,

1. A [Github](https://www.github.com) account
2. Git client installed on your machine.

## Creating the Project
Create a new repository in Github with the name “the-empty-project” with the description “A valid but empty Precision 100  project"

![Create empty project repository](./images/create-empty-project-repository.png)

Now execute the following commands.
```
git clone https://github.com/ennovatenow/the-empty-project.git the-empty-project

cd the-empty-project
mkdir dataflows
touch dataflows/project.reg
mkdir -p containers/container-one
touch containers/container-one/container.reg
mkdir -p containers/container-two
touch containers/container-two/container.reg

git add .
git commit -m "created the template"
git push origin master
```
And we have perfectly valid and empty **Precision 100** project. (Change the git url to point to the repository you have created). 



