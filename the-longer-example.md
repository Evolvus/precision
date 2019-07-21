# The Longer Example
In this example we will start by creating a simple project that executes two shell scripts. We will not be using any design tool but rather build the entire project from scratch and execute it using **Precision100**. We will be using [Github](https://github.com) as a `repository` for this project. If you don't have an account there, you should get it before going any further. We will calling our project rather unimaginatively "the longer example", with that lets get started.

## Creating the Project.
Create a new repository with the name "the-longer-example" with the description "A sample project to understand the workings of Precision 100". 

![Create a new repository](./images/create-repository.png)

Now execute the following commands.
```
git clone https://github.com/ennovatenow/the-longer-example.git the-longer-example

cd the-longer-example
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
And we have perfectly valid and of course a perfectly useless **Precision 100** project. (Change the git url to point to the repository you have created). 


The above instructions are straight forward, you create two folders at the root of the project i.e. `dataflows` and `containers`.Inside the `containers` folder we create two folders (containers in Precision 100 parlance), in this case we have named them, again very unimaginatively, `container-one` and `container-two`. 

Inside the `dataflows` and `container`s we put "`reg`" or registry files. These are special files and should be named exactly as mentioned. Each `container` should have a `container registry` file i.e `container.reg` and the `dataflows` folder must have a `project registry` file i.e `project.reg`. 

You can learn more about `registry` files and naming conventions in the best practices section of the documentation, but for now lets try to run this empty project.

## Running the-longer-example
To run the-longer-example project, execute the following,
```
git clone --recurse-submodules https://github.com/ennovatenow/precision-native.git tle-client
cd tle-client
./configure-project.sh "GIT" "https://github.com/ennovatenow/the-longer-example.git" "The Longer Example"
/init-exec.sh "mock1"
./migrate.sh
```

If things have gone well you should see a menu and your screen should look like something below,

![The longer-example menu](./images/the-longer-example-menu.png)

That was quite a lot of work to get to a menu that just says Quit, it would seem that nothing has been done. Well, Yes and No. The fact that we were able to bring up the menu indicates that this is a valid project even though it is not doing anything, yet. Lets understand the activities performened here and then we will see how to make our project do something, and add those activities to the menu.

The first thing we do to run the project is to install one of the `Precision 100' clients. The `Precision 100` framework by itself does not provide any interface to run the project, this is done by `Precision100 clients`. `precision-native` gives a menu-driven interface which can be used to run the project. 

Once the `precision-native` client is installed, we need to configure it to use our new project. This is done by invoking `configure-project.sh` script that is provided with the client. This script accepts the repositry type, which can be GIT or SVN or FILE (default GIT), the URL of the repository and the name of the project. (Remember to give the URL of your newly created project here). With this, our installation is configured to our new project. `Precision 100` can have multiple installations, but each installation can work with only one project.

Now that we have the project configured, its time to run the project. We can run our project multple times. Each run is an `iteration` so lets initialize the `iteration` and give the `iteration` a name. This is done by invoking `init-exec.sh` script provided with the client with the name of the `iteration` i.e. "mock1". This script connects to the url configured for the project and retrieves it. Now if you do `ls` on the `tle-client` folder you will see that a new folder with the same name as the `iteration` has been created and inside it you will find `local-repo` folder which has the project that you had created.

Finally we run `migrate.sh`. This interogates the downloaded project and builds the menu based on the contents of the `project.reg` registry file in the `dataflows` folder. We have not added anything to this file and hence we get nothing in the menu except the default `Quit` option.



