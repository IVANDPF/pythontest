# pythontest

## INSTALL homebrew & PYTHON
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
brew -v
brew update
brew install python3
python3 -V
Then we must have a message with our Python version

## Package Manager:pip
Even though programming languages come with a lot right out of the box, you'll find yourself wanting to use some functionality that is not included in your language's standard library. For example, since Python can be used for more than just web development, web functionality does not come pre-loaded when we install Python. However, other developers have created packages that we can download so we don't have to reinvent the wheel.

Pip is the package manager we'll use in Python to install these third-party packages. (There are other package managers, but for simplicity and fewer installations, we're sticking with pip because it was included when we installed Python.) Rather than having to go search for packages and versions ourselves, package managers are generally able to find the versions we need with just a single command from our end. That command will look like this:

###### Mac/Linux:	Windows:
$ pip3 install {{package}}	$ pip install {{package}}
<= NOTE: substitute {{package}} with the package you are installing (For this case Django)

## Install multiple packages
To install multiple packages, the following command can be used to shorten the manual installation process one by one. Inside the rp_platform folder a file named requirements.txt has been defined that contains all the packages that are being used in the project with their respective version in order to avoid compatibility problems.

###### Mac/Linux:	Windows:
$ pip3 install -r requirements.txt	$ pip install -r requirements.txt
Virtual Environments
You may have noticed that when we installed a package using pip, it was installed globally on our machine. While this is okay, if we're working on multiple projects, it might be hard to keep track of which projects are using which packages, or in other words, which projects have which dependencies. To keep this organized, Python uses virtual environments.

In addition to specifying what packages we need, we can also specify which version of Python to use in a given environment. This allows us to have multiple versions of Python installed on our computer and then easily switch between versions when actually running and testing our code.

In practice, because your projects will be larger, it's good to create virtual environments specific to a project.

We need a place to store these environments. Create folder named RP-web as environment folder. So, Let's store our environment there. In the terminal, navigate (cd) to the rp-web directory. Next, decide on a name for your environment (it can be whatever you'd like). We're naming our environment rp. Here's the command to create the virtual environment with that name:

###### Mac/Linux:	Windows:
python3 -m venv Rosaprima	python -m venv Rosaprima
We should now see a new folder in our previously empty rp-web directory called rp.

## Activating a Virtual Environment
The keyword for activating a virtual environment is source or call, depending on which OS and terminal we're using. We run this command and specify which environment to activate like so (the following assumes we are in the rp-web directory, with a virtual environment called rp):

###### Mac/Linux:	Windows:
source Rosaprima/bin/activate	call Rosaprima\Scripts\activate
We know our virtual environment is active, and which virtual environment is active, when the command line changes to something like this: (rp) $

Moreover, if you type pip3 list in Mac/Linux and pip list in Windows you must see Django installed as a package.

## Deactivate a Virtual Environment
To deactivate a virtual environment, just type deactivate in the command line. Closing your terminal window will also deactivate your virtual environment.

Run Django "ROSAPRIMA-PLATFORM" project
With our Django virtual environment activated, run this command:

###### Mac/Linux:	Windows:
python3 manage.py runserver	python manage.py runserver
Open http://127.0.0.1:8000/ in a browser window. Hooray for CLIs (command-line interfaces)! (Don't worry about the warning about unapplied migrations. It won't affect us for now, and we'll address it soon enough.)

Press ctrl-c to stop the server. Open up the project folder in your text editor. (Take note of the folder structure so far!)

Create an application in the project "ROSAPRIMA-PLATFORM".
To carry out file management in a more organized way, it is advisable to manage folders or also named in the Django framework as applications.

###### Mac/Linux:	Windows:
python3 manage.py startapp {{application_name}}	python manage.py startapp {{application_name}}
<= NOTE: replace {{application_name}} with the name of the application you are going to create (in this case it is rp_home)

## Migrations in Django
If, when running the project locally, you see a message on your console like the following: You have xx unapplied migration (s). Your project may not work properly until you apply the migrations for app (s): admin, auth, contenttypes, rp_register, sessions. You will need to run the following command to apply the pending migrations.

###### Mac/Linux:	Windows:
python3 manage.py migrate	python manage.py migrate
Create the "static folder" of files for deployment
As a previous step for the deployment on a server, the "static folder" must be generated, this folder contains all the js, css, images, among others, and serves for the correct visualization and operation of the website.

###### Mac/Linux:	Windows:
python3 manage.py collectstatic	python manage.py collectstatic