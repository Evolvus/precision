# Using the **Precision 100** framework without *git*
In most of the examples we use [Github](https://github.com) as a repository and *git* client to connect to it. However, this is not mandatory, **Precision 100** framework can work with the file system just as easily it does with *git*. 

It is a best practice to have a repository server hosting the project. Developers can work safely to make changes to the project. However there are circumstances where access to a repository is not possible because of security or other reasons. **Precision 100** comes with the *file-repo-operator* which allows you use the file system as a repository, ofcourse with this, you loose the benefits of a source control system and changes should be done very carefully.

Let us run the [the-longer-example](./the-longer-example.md) without *git*. To do this we need to have the *precision-native* and *the-longer-project* zip archives. Extract the *the-longer-project* archive to a folder, say, *the-longer-project*. Similarly extract the *precision-native* archive into a folder, say, *tle-client*

```
cd $HOME
unzip precision-native.zip -d tle-client
unzip the-longer-example.zip -d the-longer-example
```

Now to configure the project to point to the folder containing `the-longer-example` project do the following,

```
cd tle-client
./configure-project.sh "FILE" "../the-longer-example" "The longer example"
```

And we are done. We need to pass the first parameter as *FILE* instead of *GIT* which we have been using most of the time. The second parameter is the path to the folder containing the project instead of a git url. When we start an `iteration` the *file-repo-operator* copies the contents of the folder whose path is mentioned as the second parameter to the *local-repo* folder. Any change made in *the-longer-example* folder will not reflect here till the next `iteration` - just as it happens with the *git* client.

And there you have it, Using the **Precision 100** framework without *git*.
