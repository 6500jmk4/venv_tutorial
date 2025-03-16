# Using `venv`
This program is written for Unix machines (Linux and Mac OS). It should also work for Windows machines, keeping in mind slight variations in the command line. For example, on Unix machines, a path to a file is written as `path/to/file`.  On Windows machines, it is written as `path\to\file`. See [the Python documentation](https://docs.python.org/3/library/venv.html) for other variations.   

## Virtual Environments
When developing programs with Python, it is usually good practice to use a virtual environment. A virtual environment allows you to create an isolated directory where you can keep all of the specific dependencies (software libraries) for your program. This allows you to use specific versions of your interpreter (i.e. your version of Python) and its dependencies without changing your global Python settings. 

`Venv` is one of numerous programs that allow you to create virtual environments (others include, `virtualenvs`, Anaconda and Conda, `pyenv`). The benefit of `venv` is that it is part of Python 3.3 and newer. It is a lightweight program and relatively easy to use. 

`Venv` is not meant to be moved or copied (it uses paths specific to your computer), and because of this, it should be added to the `.gitignore` folder when using `git`.

The steps below outline how to set up your `venv` environment and include best practices for making it reproducible by other users.

## Create a Virtual Environment

1. Navigate to the folder where you would like to create your project. If necessary, create the folder.
2. Create a virtual environment using `venv`:

```
python -m venv ./any_path/my_project-venv
```

This command does several things:
- `python -m venv`: tells the computer to use python and run module (`-m`) named `venv`
- the `./any_path/my_project-venv` is the path to where you want to keep your `venv` directory.
- You can name your `venv` directory anything you want, but good practice would be to name it after your project, which is why I use the `my_project-venv` naming convention. 

## Setup Your `venv` Environment

You `venv` environment is now ready to be set up. You may not automatically see it in the file directory, but if you type `ls -a` in the command line, you should be able to see it. 

### Activate Your Environment
To activate your new `venv` environment, enter the following into the command line

```
source my_project-venv/bin/activate
```

You will see that the command prompt now displays your virtual environment. 

Now that you are in your virtual environment, you can begin setting it up. 

### Using `pip` to Install Dependencies
When you are working in Python, you will be installing dependencies. Dependencies are external packages that you need in order to run your program. Some common dependencies include `NumPy` and `Pandas. 

To install dependencies, Python provides the `pip` package installer. You install a dependency as follows:

```
pip install pandas numpy
```

This command installs both the `Pandas` and `NumPy` packages. 

### Setting up a `requirements.txt` File
Because you will not be transferring your `venv` directory between computers and users, you need to set up a file that provides directions on how to reproduce your configuration on other computers. The best practice for doing this is setting up a `requirements.text` file. 

Creating this file is simple. Enter the following into the command line:

```
pip freeze > requirements.txt
```
The `pip freeze` command adds a list of all installed packages (and versions) to a file named `requirements.txt.

If you have installed `pandas` and `numpy` the contents of your `requirements.txt` file will look something like this:

```
numpy==2.2.3

pandas==2.2.3

python-dateutil==2.9.0.post0

pytz==2025.1

six==1.17.0

tzdata==2025.1
```

Each time you add a new dependency, you will want to update your `requirements.txt` file by running `pip freeze > requirements.txt`.

When you want to recreate the setup for your virtual environment in another folder, or on another computer, you can transfer the `requirements.txt` to the new environment and then type the command:

```
pip install -r requirements.txt
```

This will tell `pip` to pull the exact dependencies and versions you need.


### Adding `venv` to Your `.gitignore` File
If you use Git for version control, you will want to add your `venv` folder to your `.gitignore` file. `.Gitignore` tells Git to ignore files and folders when it is constructing its versioning database. 

You will want to tell it to ignore your `venv` folder, because the `venv` folder is both meant to be temporary and specific to your computer's setup. If you use Github, you will not want to share it as part of your code and assets.

Since Python 3.13, `venv` should create a `.gitignore` file default. You can check by opening the `.gitignore` file. If it is not in the `.gitignore` file, follow the directions below. 

To add your `venv` folder to your `.gitignore` file, open `.gitignore` and add
```
my_project-venv/
```

This will tell Git to ignore the `venv` folder and everything within it. 

If you forget to do this, and Git is already tracking your `venv` folder, you can run the following command to remove it:

```
git rm --cached -r venv
```


### Deactivating Your `venv` Environment
When you have completed work on your `venv` environment, you can deactivate it via the command line:
```
deactivate
```

Your computer will return you to your default shell (bash, zsh, etc.). To restart your virtual environment, you simple type `source my_project-venv/bin/activate`.

## More Information
For more information on `venv`, see the Python documentation at https://docs.python.org/3/library/venv.html. 
