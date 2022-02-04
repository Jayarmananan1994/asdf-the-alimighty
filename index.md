# ASDF - The almighty

Once I happened to work on a legacy project which was using an older version of java. However I like to keep the java version updated in my system and fiddle around with new feature present offered by newer versions. And it was kind of a mess to switch the java version between the projects. 

![](https://favbulous.com/wp-content/uploads/2013/12/animals-who-are-terrible-at-judging-distances-2.gif)

That's when I got introduced to `asdf` by a fellow Thoughtworker.

![](https://media3.giphy.com/media/IdrRAjS9jfD9dqQjAn/giphy.gif)

`asdf` is a tool that will help you manage multiple runtimes like java, ruby, nodejs in a single CLI.

## Getting started with asdf
_Note:_

_1. For sake of brevity, here I am describing here the scenario of MacOS + brew combo_\
_2. For Ubuntu, you can find installation step here [here](http://asdf-vm.com/guide/getting-started.html#_1-install-dependencies)_\
_3. Similarly, installing runtime other java also should be fairly straight forward. For example if we need to install nodejs just replace `java` with `nodejs`_. 

### 1. Installing asdf

```shell
  brew install asdf
```
### 2. Run below commands to complete the installation.

```shell
#If you are using bash profile
echo -e "\n. $(brew --prefix asdf)/libexec/asdf.sh" >> ~/.bash_profile
echo -e "\n. $(brew --prefix asdf)/etc/bash_completion.d/asdf.bash" >> ~/.bash_profile

#If you are using zsh shell 
echo -e "\n. $(brew --prefix asdf)/libexec/asdf.sh" >> ${ZDOTDIR:-~}/.zshrc
```
Now if you run `asdf` command in your terminal, you ll get a bunch of helpful command along with a punch line from **Superstar**.

![](https://c.tenor.com/ED0zRcr1x8kAAAAd/rajinikanth-superstar.gif)

### 3. Installing Plugin.

The next step would be to install the plugin that will let you install the actual runtime and manage them. Each runtimes would have its dedicated plugin. Let's say if I want to install java, then i need to install the asdf-java-pluign as below.

```shell
asdf plugin-add java https://github.com/halcyon/asdf-java.git
```

### 4. Installing the runtime.

Let's install any version of runtime that we need. For example, to install java 8 sdk, you can run the below command.

```shell
asdf install java adoptopenjdk-8.0.312+7
```
You can replace `adoptopenjdk-8.0.312+7` with any version that you wish to install.

You can also do something like below.
```shell
 asdf install java latest
```
which will install the latest stable version of the sdk.

Wondering how I can find the suitable sdk/runtime version? Just run the below command.
```shell
asdf list-all java 
```
This would list down all the versions available for installing. 

If you want to list down all the versions installed locally, use any of the commands below.
```shell
asdf list java
```
```shell
asdf shim-version java
```
### 5. Configuring the runtime

Now that we have downloaded the SDK, let's use them. asdf provides us the flexibility to configure the runtime to local and global level. Lets say if I want to configure java 8 for a particular project, just `cd` into the project directory and execute the below command.

```shell
asdf local java adoptopenjdk-8.0.312+7
```

To set the version globally, we can execute below command.
```shell
asdf global java adoptopenjdk-8.0.312+7
```
By this way, we can maintain a different java version without any conflict :star_struck:

One thing to point out is, when you configre a runtime version inside project it generates a `.tool-version`. This single config file generated per project will manage the runtime version of the project. You can also configure `asdf` to use the `.ruby-version`, `.nvmrc` file instead of `.tool-version` file.

## And finally,

There is no problem with the package manager like npm, rbenv etc. They are great tools on their own and do their job. But personally I felt `asdf` is making developers' lives easier and brings a unified approach in maintaining different runtimes. `asdf` is not without any caveats. Below are few things that I noted (Can't say as issue completly).

* asdf may not work as expected for a language, if you already have a package manager specific to that language/runtime. For example, I had an issue with handling ruby runtime using `asdf` in a system where `rbenv` is already installed.
* Some of the runtime might need extra prerequisite dependencies.
* Some may need extra step post installation.

Despite all of that, I still feel it is an awesome tool and would recommend any developer who works in ubuntu, Mac to have it in their kit. So far I was able to manage java, nodejs, ruby runtime easily with `asdf` and from my brief experience of using `asdf` I would weigh it as good as `brew` for a mac user. Thanks to those awesome people who contributes `asdf` I am  jumping around different runtime happily.

![](https://thumbs.gfycat.com/DefenselessWickedAmericanwirehair-size_restricted.gif)


