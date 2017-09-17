# A Brief History
We'll start with a brief history of version control so that we can understand where we've come from and how we got to where we are now. The very first version control systems were developed in the early 70s and operated on a single file and had no networking support. These were systems such as SCCS and RCS. They operated on a single file so you can have a file such as foo.c and how multiple versions of that file, but there was no correspondents between different files within a repository. There was no notion that version 1.1 of foo.c went with version 1.1 of bar.c, it could be arbitrary. So, we only had single files. This lead to the obvious innovation of having a multi-file system or the second generation and this is simplified by centralized version control systems such as CVS, Visual SourceSafe, Subversion, Team Foundation Server, and Perforce. All of these are multi-file centralized systems so you can check out into a working copy on your local system all the files necessary for particular version of a repository. Along came the third generation which are the distributed version control systems such as Git, Mercurial, Bizaar, and BitKeeper. These work on changesets. These changes sets can be shift around and both clients and servers can have the entire repository present which allows us to do some interesting things. So, you can see this gradual evolution of going from single file to multi-file to changesets. Going from no networking such as centralized to a distributed and all the additional capabilities that get added with these new generations, a version control systems. If you want to read more about the history of version control, I will refer you to Eric Sink's article at this address.

# Installing Git
Installing Git client is essential to work with server
## Windows
I would recommend using the msysgit project. Let's install git onto Windows. We are going to use the msysgit project and I can go to the Downloads tab and I'm going to download the very latest, so this is the full installer for Git 1.7.10
## Linux
In debian systems use apt-get to install git-core
```bash
 $ sudo apt-get install git-core
```
# Configuring Git
Configuration of git are present in config file
Git has configuration at three levels
- System level
 - Configuration that effects all the users
 - Configuration file is located at /etc/gitconfig
- Global (User level)
 - Configuration this specific to user
 - Configuration file is locat at /home/{user}/.gitconfig
- Local (Repository level)
 - Configurations specific to Repository
 - Configuration file for **demo-repo** repository at /home/ubuntu/demo-repo/.git/config


## List configuration
List all the configurations at **system** level
```bash
$ git config --system --list
user.name=Padma Chopparapu
```
is equivalent to
```bash
$ cat /etc/gitconfig
[user]
        name = Padma Chopparapu
```
List all configurations at **user** level

```bash
$ git config --global --list
user.name=padma
user.email=padma.ch@gmail.com
```
is equivalent to
```bash
$ cat ~/.gitconfig
[user]
        name = padma
        email = padma.ch@gmail.com
```
## Add configuration
To add configuration at **global(user)** level
```bash
 $ git config --global user.name "Padma Chopparapu"
```
Few important configurations

Property|Value|Remarks
--------|-----|------
user.name|padma ch| user name with which user is authenticated
user.email|padma.ch@gmail.com| user email address
core.editor|vim|Your core editor is the default editor that you want to use when editing commit messages or viewing diffs and other pieces of information from git.
help.autocorrect|30| Wait for three seconds before it runs autocorrected command. Set to **0** do disable auto correct
color.ui|auto| If it's running within a script then it will not put out any output color, output escape sequences so that logs are easier to pars, but if it is detected as running within the terminal it will output the escape code to colorize the output.


*Config sources are hierarchical. The user-level one overwrites any system level settings and repo-level settings overwrite user-level settings.*

### Git auto correct example
```bash
$ git statsu
WARNING: You called a Git command named 'statsu', which does not exist.
Continuing under the assumption that you meant 'status'
in 0.5 seconds automatically...
On branch master
Initial commit
nothing to commit (create/copy files and use "git add" to track)
```

## Remove configuration
Remove auto correct configuration
```bash
$ git config --global --unset help.autocorrect
```
