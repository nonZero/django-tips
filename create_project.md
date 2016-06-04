# Creating a New Django Project

In this document we will explain how to create a new project called
*myproject*. 

## Prerequisites
* Make sure you have Python 3.5 installed and running from the command line. Check it out by running `python3 --version`.
* Make sure you have `pip` installed.  Check it out by running `pip3 --version`.
* Install **virtualenvwrapper**:
    * On ubuntu linux:
        * Run `sudo apt-get install virtualenvwrapper`.
        * Close all your terminal windows.
    * On arch linux: Follow installation instructions 
      [here](https://wiki.archlinux.org/index.php/Python/Virtualenv#Virtualenvwrapper).
    * On any other linux / mac: Follow instructions 
      [here](http://virtualenvwrapper.readthedocs.io/en/latest/install.html).
    * On windows: Run `pip3 install virtualenvwrapper-win`
     

## Create a virtualenv for your project
We will start by creating a clean virtual copy (virtualenv) of python 3.5 with
no packages installed into it.

In this example it will be called *myenv*, but it can be called *myproject*
(better) or any other name you choose.

Keep in mind this is **different** from your project (source code) folder.

* On windows, or if your default python is python 3.x, run:
     
        mkvirtualenv myenv

* On ubuntu, or if your default python is **not** python 3.x, run:
     
        mkvirtualenv myenv -p $(which python3)
     
This will create a "shallow" copy of python in the following path:

* Linux/mac: `~/.virtualenvs/myenv/`
* Windows: `C:\Users\MyUser\Envs\myenv`

Usually you should not modify the contents of this folder manually - packages
will be installed here using the **pip** package manager.

This also **activates** the virtualenv by modifying your *path* environment 
variable.

Try running:

* Linux/Mac: `which python`
* Windows: `where python`

You can see the path of the python executable is inside your virtualenv.

You can also notice your command prompt have changed and now starts with
`(myenv) ` to reflect the fact you are using python inside this env.

In the future, when you open a new terminal, and would like to **activate**
the virtualenv again, just run:

    workon myenv

You can also visit the folder containing all installed packages (currently 
none) by running the command:

    cdsitepackages
    
or show the list of packages with:

    lssitepackages

     
## Install Django

To install django on your new virtualenv, run:

    pip install django

If this works correctly, you should be able to run the following command:
 
    django-admin

We highly recommend to install also ipython:

    pip install ipython

On windows *pyreadline* would be needed as well to make ipython work correctly:

    pip install pyreadline

Optionally install jupyter notebook (previously known as ipython notebook):

    pip install noteboook


## Create A Root Folder For Your Project
Now we will create a root folder for the project.  Start by going to the folder holding all
your projects, in my case:

    cd ~/projects

A django project always includes one **python package module** to hold project
settings and some more stuff.  By convention, if your project is called
`myproject` this package will be called `myproject` as well, i.e. **inside**
our project root folder we are going to have a `myproject` folder with a 
`__init__.py` file inside it.

However, we do not need to call the root folder the same.

**I highly recommend to call your root folder `MyProject` instead.**

This folder would also include your `.git` folder and other stuff.

To create your project root folder run:

    mkdir MyProject

## Create The Project 

Now use the *django-admin* command to create the project base structure inside:

    django-admin startproject myproject MyProject
    
The command above created a simple skeleton for your project:

    MyProject/
       - manage.py
       - myproject/
            - __init__.py
            - settings.py
            - urls.py
            - wsgi.py

## Create a git Repository for your project 
Run:
    
    cd MyProject
    echo __pycache__ > .gitignore
    git init
    git add manage.py myproject
    git commit -m "initial commit"

            
## Create a PyCharm Project
If you have installed the charm command line shortcut:

* `cd` into `MyProject` folder, and run `charm .`.
* In pycharm settings dialog, in the project interpreter panel, choose
  "Add local..." and `~/.virtualenvs/myenv/bin/python`. 

Otherwise:

* In PyCharm, choose *File> New > Project*.
* In the *New Project* dialog:
    1. Select the `MyProject` folder as your poject root.
    2. Set up a new interpreter by clickong on the gear/cogwheel icon and
     choosing "Add Local.." and selecting your virtualenv's python:
        * On Linux/Mac: `~/.virtualenvs/myenv/bin/python`.
        * On Windows: `C:\Users\MyUser\Envs\myenv\Scripts\python.exe`.

Make sure Django Support is activated in *Settings > Languages and Frameworks >
Django*:

    * Select `MyProject` as your project root.
    * Select `myproject.settings' as your settings module.
    * Select `manage.py` as youre manage script.

## Take a look at the files.
What you are looking for is in `myproject\settings.py`, which in python is 
referred to as `myproject.settings`.

You can see `myproject.settings` is used in `manage.py` and `wsgi.py` for
example.


## Start The Developmnet Web Server
Run:

    python manage.py runserver

In linux/mac you can also run:
    
    ./manage.py runserver

In windows you can also run:
    
    py manage.py runserver
    
In your browser, go to: <http://127.0.0.1:8000/> .
 
To stop the server press <kbd>Ctrl</kbd> + <kbd>C</kbd>

It is recommended to start the server from within PyCharm.  Make sure it is not
running from the command line and from `Run > Edit configurations` click on the
plus icon and choose *Django Server*.  Call it `runserver 8000` and use it to run the
server from the Run dropdown menu in the toolbar.
