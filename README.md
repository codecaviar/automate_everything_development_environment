<img src="https://raw.githubusercontent.com/codecaviar/digital_asset_management/master/assets/bingyune-and-company-logo-6400x3600.png" align="left" width="200" height="auto">

<br/><br/><br/><br/>

----------

# Automate Everything: 3 Super Tips to Setup Development Environments

## Project Overview

A development environment in data science and engineering is a workspace for developers to make changes without breaking anything in a live, production environment. You should use a development environment on a local machine or server, where the production code is downloaded, so it is ready to be changed and modified. However, setting up your own development environment gives you the opportunity to learn how to code on your computer and create personal projects.

**The goal of this project is** to provide guidance for data scientists and engineers to manage their projects in a solid and reproducible manner by using 3 key tools: `unix shell`, `conda`, and `git`. By the end of this guide, you are going to be able to access  create a git repository, version your scrips/datasets/models, and replicate the same development environment on new machines.  

## Summary:

1. **UNIX Shell** -  almost all cloud computing platforms like Google Cloud Platform or Amazon Web Services are Linux based (use a flavor of Unix Shell), which is useful for tasks such as navigating directories, copying files, and using virtual machines.
2. **Anaconda or Miniconda** — your package and environment manager, a Python data science distribution with a collection of relevant open-source packages
3. **Git and GitHub** — version your projects with one of the best version control systems for tracking changes, and optimizing collaborative developments

**Bonus:** [Atom](https://atom.io/) is a hackable text editor for the 21st century, built on atom-shell, and based on everything we love about our favorite editors. Just about anything that can edit plain text will work for writing Python code; however, using a more powerful editor may make your life a bit easier.

### Unix Shell

A Unix Shell provides you with an interface to the Unix system. It gathers input from you and executes programs based on that input. When a program finishes executing, it displays that program's output. The command prompt, `$`, is issued by the Unix Shell. While the prompt icon is displayed, you can type a command. A Unix Shell reads your input after you press `Enter`. It determines the command you want executed by looking at the first word of your input. A word is an unbroken set of characters. Spaces and tabs separate words.

```
pwd # use to print the working directory

ls # list all files in current directory  

cd diff_directory # change working directory
cd .. # move back one directory  

mkdir new_directory # make a directory

cp file_name new_directory # copy file into directory
cp file_name file_name.bak # make a backup of a file

rm file_name.bak # remove files or directories
rm *.tmp # remove all files of a specific format

mv old.md new.md # move or rename files
```

Modern cloud computing systems are Linux based (i.e. use some type of Unix Shell). For instance, if you want to setup a data science environment on [Google Cloud Platform](https://www.datacamp.com/community/tutorials/google-cloud-data-science), or do deep learning with `jupyter notebook` on [Amazon Web Services](https://www.datacamp.com/community/tutorials/deep-learning-jupyter-aws) it requires some Unix Shell knowledge. You will often also find Unix Shell commands integrated in other technologies alongside Python code. For example, in `jupyter notebook`, you can access shell commands by escaping to the shell by using an `!`. [Jupyter Notebook](https://jupyter.org/) is an open-source web application that allows you to create and share documents that contain live code, equations, visualizations and narrative text.

When using `Mac OS`, a Unix shell is installed by default as the [Terminal](https://support.apple.com/guide/terminal/open-or-quit-terminal-apd5265185d-f365-44cb-8b09-71a064a42125/mac)). When using `Windows`, you can install Git (see below) with the optional Unix tools so that you can have Unix commands on your [Command Prompt](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/windows-commands).

Here is a cheatsheet for common [unix shell commands](./bash_unixshell_cheatsheet.pdf).

### Anaconda and Miniconda

Anaconda is an open-source Python distribution manager for large-scale data analytics. The package and environment manager includes the core Python language (use version of your choice such as 2.7.x vs current), over 1000 data science packages (`numpy`, `pandas`, `scipy`, `matplotlib`, and `statsmodels`). On the other hand, Miniconda is a slimmed-down version of Anaconda, which decreases the download size and setup time. We recommend installing Miniconda using the following steps:

1. Go to the Miniconda download page: [Miniconda](https://conda.io/miniconda.html)
2. Select the Python installer for your computer’s operating system
3. Locate the installer that you downloaded using Finder (`Mac OS`) or Explorer (`Windows`)
4. Run the installer. Use the following instructions based on your computer’s operating system. For instance, when using `Mac OS`, open your terminal and navigate to the folder where you downloaded the installer and type the following command in the terminal: `bash miniconda-filename.sh` (you can press `Enter` and type `yes` when necessary). Note that `miniconda-filename.sh` is a fictional file name in the example above. On the other hand, when using `Windows`, follow the installation instructions provided by the installer.

You can see a list of all the packages that Miniconda installed (and test whether your installation was successful) by typing the following command into your terminal to list all environments: `conda list`

### Creating Conda Environments

Type the following command in your terminal to create an environment:
```
conda create --name conda-env python=3.8   # or use -n
```
Note you need to replace `conda-env` with the name of your environment. The `python=3.8` expression is used to specify a different version of Python.

You can also use `conda activate conda-env` to activate your environment and `conda deactivate` to deactivate the environment.

From inside an active environment, you can create an environment file (`environment.yml`) with the exact list of all the packages and version numbers installed in your project's environment:
```
conda env export --file environment.yml
```

Given an `environment.yml` file, you can easily duplicate or recreate an environment by typing the following command in your terminal:
```
conda env create -n conda-env -f /path/to/environment.yml
```

### Installing Python Packages

The Python language does not come pre-installed with all of the data science features you might want (or require) for your project. When you need specific functionality, you can install Python *packages*. A package organizes Python *modules*, which contain pre-written code that was developed by other developers (i.e. open source code). Usually `pip` is used to install and manage Python packages, but the Anaconda or Miniconda package manager is `conda`. We recommend installing all the packages you want to include in an environment at the same time to help avoid dependency conflicts (`conda` does its best to ensure dependencies are satisfied). Moreover, if a package isn’t available from the default [Anaconda Repository](https://repo.anaconda.com/), you can try searching for it on [Anaconda Cloud](https://anaconda.org/), which hosts Conda packages provided by third party repositories like [Conda-Forge](https://conda-forge.org/). As `pip` packages do not have all the features of `conda` packages, we strongly recommended to install packages with `conda` whenever possible.

Type the following command inside your active environment:
```
conda install package_name=1.4.3
```
Note you need to replace `package_name` with the name of your environment. The `=1.4.3` expression is used to specify a different version of the package.

Type the following command inside your active environment to open up a Juptyer Notebook session in your default web browser: `jupyter notebook`. Notebooks have become popular on data science projects for doing data wrangling and visualization, as it offers a great way to dynamically explore your data. Access notebook files that end with the `.ipynb` extension.

Here is a cheatsheet for common [conda commands](./conda_cheatsheet.pdf).

### Git and GitHub

Git is the most widely used version control system for data science and engineering - records changes to a file or set of files over time so that you can recall specific versions later. Git is an important technology as it really helps you collaborate with others.

When using `Mac OS`, the easiest way to install Git is to simply run `git` from the terminal for the very first time. Type the following command in your terminal: `git --version` to check the current version of Git. However, if you don't have Git already installed, the terminal will prompt you to install it.

When using `Windows`, the official Git build is available for download on the [Git website](https://git-scm.com/download/win).

### Create a GitHub Repository

The easiest way to get started with Git is to create an account on [GitHub.com](https://github.com/) - it's free. Pick a username enter your email address and a password, and click Sign up for GitHub. A repository is like a place or a container where something is stored; in this case we're creating a Git repository to store code. To create a new repository, select New Repository from the `+` sign dropdown menu (in the upper-right corner of the active window) and click Create Repository.

Type the following command inside your active directory to turn a directory managed by the Git program:
```
git init
```
Then, to tel the Git program you care about this file and want to track any changes from this point forward, type the following command:
```
git add file_name # to add a specific file
git add . # to add all files in the directory
```

A Git commit can be thought of as a milestone. Every time you accomplish some work, you can write a Git commit to store that version of your file, so you can go back later and see what it looked like at that point in time. Whenever you make a change to your file, you create a new version of that file, different from the previous one. Type the following command inside your active Git directory, after you've added files you want to track changes:
```
git commit -m "first commit" # you must always write a message
```

Type the following command inside your active Git directory to connect your computer to GitHub:
```
git remote add origin https://github.com/<your_username>/directory_name.git
```
We are telling Git to add a remote called origin with the address `https://github.com/<your_username>/directory_name.git` (i.e., the URL of your Git repo on GitHub.com). This allows you to interact with your Git repository on GitHub.com by typing origin instead of the full URL and Git will know where to send your code. Type the following command inside your active Git directory to push commit changes:
```
git push origin # add changes and commit message to URL
```

Here is a cheatsheet for common [Git commands](./git_cheatsheet.pdf).

### Conclusion

The guide provides a way to setup a local data science and engineering environment on your local computer. An important point to emphasize is that these technologies can and are often integrated together. If you have any questions or thoughts on the guide, please reach out to us via support(at)bingyune(dot)com. Also, we invite you to check out our other guides located on GitHub @codecaviar.

## Authors

- **BingYune Chen** - [LinkedIn](https://www.linkedin.com/in/bingyune-chen/)
- **BingYune & Co** - [GitHub](https://github.com/codecaviar)

## License

The project is licensed under the GNU General Public License v3.0 License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

The project referenced the following resources:
* https://towardsdatascience.com/get-your-computer-ready-for-machine-learning-how-what-and-why-you-should-use-anaconda-miniconda-d213444f36d6
* https://towardsdatascience.com/a-guide-to-conda-environments-bc6180fc533
* https://www.codecademy.com/articles/install-python

----------
The Code Caviar is a digital magazine about data science and analytics that dives deep into key topics, so you can experience the thrill of solving at scale.
