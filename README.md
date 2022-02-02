# ASDF - The almighty

Once I happen to work on a legacy project which was using an older version java. However I like to keep the java version updated and fiddle around with new feature 
present offered by newr versions. And it was kind of a mess to switch java version between the projects. Thats when i got introduced to `asdf` by a fellow Thoughtwoker.

`asdf` is a tool that will help you manage multiple runtimes like java, ruby, nodejs in a single CLI.

## Getting started with asdf
_Note: For sack of  breivity, here i am lisitng only the steps required for MacOS + brew combo._

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
Now if you run `asdf` command in your terminal, you ll get a bunch of helpful command along with a punch line from Superstar.

![](https://c.tenor.com/ED0zRcr1x8kAAAAd/rajinikanth-superstar.gif)

### 3. Installing Plugin.

The next step would be to install the plugin that will let you install the actual runtime and manage them. Each of the runtime would have their own plugin. Lets say if I want to install java, then i need to install the asdf-java-pluign as below.
```shell
asdf plugin-add java https://github.com/halcyon/asdf-java.git
```

### 4. Installing the run time.

Let's install version of the runtime that we need. For example to install java 8 sdk, you can run below command.

```shell
asdf install java adoptopenjdk-8.0.312+7
```
You can replace `adoptopenjdk-8.0.312+7` with any version that you wish to install.

You can also do something like below.
```shell
 asdf install java latest
```
which will install the latest stable version of the sdk.

Wondering how can i find the suitable sdk/runtime version? Just run the below command.
```shell
asdf list-all java 
```
This would list down all the version avaialble for installing. 

If you want to list down all the versions installed locally, use any of below command.
```shell
asdf list java
```
```shell
asdf shim-version java
```






