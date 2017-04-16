# GenericFlaskEnv Notes

Setup a generic Flask virtual environment.

## Goals:
1. Setup a python virtual environment called flask in the project folder
2. Install the packages from the [Flask mega Tutorial][flaskMegaTutorial]
3. Do helloworld example to show it works
4. Setup a dependencies file
5. Upload to github

## Other:
* virtual environment support for python scripts by clicking or via calling
py filename.py from the commandline (uses shebang notation at top of python file)
* activate a venv so it uses the locally installed version of Python when calling it from the command line


## Notes:
### Virtual Environment in 
* [virtual environment tools python summary][venvToolsSummary]
* [Virtual environments][theHitchhikersGuidetoPython]
* My local installation of python is 3.5.2 via the Anaconda 64 bit version for windows
* it seems anaconda doesn't come with the python file launcher for windows, need to get 
a py.exe file and add it to the windows system directory ([started from shebangs in flask tutorial file][shebangsSO], 
then t0 [find the pylauncher][pylauncherWinSO]). This method was altered in 3.6 as python
is installed in a different location. I can now:
    - call: python --> local anaconda python version (64 bit)
    - call: py --> local python 3.6.1 version (is 32bit?)
    - call: py filename.py --> opens with shebang to correct python version from venv for example  
    general [info][pyLauncherInfo] about the pylauncher     
* [activating a venv][soVenvActivate] helps set the right version of python when calling it for a commmand line session
    - call: python --> this should actually use the local venv version
    - after activation, call: py --> use local [venv version of python][soVenvActivate2] (shows up venv name in command line)  
    The shebang method works only for calling scripts. [Other discussion pylauncher and association.][soVenvAss]
* [other things to look into is autoenv and environmentwrapper][autoEnvWrapper]
* [Venv and git][vEnvGit]
* activate venv: venv\Scripts\activate (this is a batch file, this works without venvwrapper)
* bind project folder with venv: inside activated venv: setprojectdir .
* [atom and virtualenv][virtualenvAtom]

### Dependencies
* [rhode schwarz vna][rsVna] has an example of setup.py for dependencies of python project, also check out vagrant/
* [python packages and dependencies][pyPackDep]
* [Fullstack Python application dependencies][fsPyAppDep]
* [git list tracked files][gitTracked]
* [pip freeze][pipFreeze]: 
    - Running pip freeze in my project results in a laundry list of dependencies. 
    - Only when running it with the Venv activated did it give the right list! before it just
    gave a list of all the dependencies of my anaconda python installation. I noticed
    it because I didn't install all of the flask tutorial packages that time.
    - Some of the dependencies will probably be installed automatically by going through
    the list (i.e. I expect installing flask will install jinja2 templates)
    - list of all dependencies by pip freeze (bold ones are from tutorial installed explicitly):
        * Babel==2.4.0
        * blinker==1.4
        * click==6.7
        * **coverage==4.3.4**
        * decorator==4.0.11
        * defusedxml==0.5.0
        * **Flask==0.12.1**
        * **Flask-Babel==0.11.1**
        * **Flask-Login==0.4.0**
        * **Flask-Mail==0.9.1**
        * **Flask-OpenID==1.2.5**
        * **Flask-SQLAlchemy==2.2**
        * **Flask-WhooshAlchemy==0.56**
        * **Flask-WTF==0.14.2**
        * **flipflop==1.0**
        * **guess-language==0.2**
        * itsdangerous==0.24
        * Jinja2==2.9.5
        * MarkupSafe==1.0
        * pbr==2.0.0
        * python3-openid==3.1.0
        * pytz==2017.2
        * six==1.10.0
        * SQLAlchemy==1.1.8
        * **sqlalchemy-migrate==0.11.0**
        * sqlparse==0.2.3
        * Tempita==0.5.2
        * Werkzeug==0.12.1
        * Whoosh==2.7.4
        * WTForms==2.1
    - installing dependencies from requirements: pip install -r requirements.txt
    - for libraries you use a setup.py file, setuptools

### Setting up git for the project
* [creating a .gitignore file][gitIgnore]: read for untracking files
* [Starting web projects using Flask][enigmetaFlask]: WSGI script, Fabric deployment
* undo git staging: git reset
* stage all: git add .
* check .gitignore file is correct. can I ignore all files in venv folder?
* [push project to github][githubPush]

### Setting up project
* clone repository from git: git clone https://github.com/rschutjens/genericFlaskEnv.git
* cd genericFlaskEnv
* create a virtualEnv in the directory: virtualEnv flask (tested with python 3.5.2 64 bit anaconda custom version)

If created with virtualenvwrapper you'll activate the environment immediately. The command
line tool usually indicates it. 
You can check the version of python is active, powershell: python -V, bash: which 
python. If it is not the environment one, activate it, powershell: .\flask\Scripts\activate, 
bash: source flask\\Scripts\\activate.
there is different options if you use virtualenvwrapper, like workon

* install packages: pip install -r requirements.txt
* you should now be able to run: python run.py 
* open up a browser and go to http://127.0.0.1:5000/

Note: run.py has a shebang line that automatically uses the python from the virtualenv
named flask (this path also depends on your operating system, the one provided is for
windows #!flask\Scripts\python). The shebang will only work on windows with the pylauncher
installed (if you installed python with anaconda it is not provided, use a standard 
installed python)
You can set up a virtual environment with virtualenvwrapper too.

alternatively you can start the flask application by (using powershell):
* activating the virtualenv: flask\Scripts\activate
* $Env:FLASK_APP=".\run.py" ([see here for powershell commands][powershellCommands])
* flask run (or [flask shell, this can be used to make interactive session][flaskShell])



[flaskMegaTutorial]: https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world
[theHitchhikersGuidetoPython]: http://python-guide-pt-br.readthedocs.io/en/latest/dev/virtualenvs/
[shebangsSO]: http://stackoverflow.com/questions/7574453/shebang-notation-python-scripts-on-windows-and-linux
[pylauncherWinSO]: http://stackoverflow.com/questions/30794342/python-windows-where-is-the-python-launcher
[pyLauncherInfo]: https://www.python.org/dev/peps/pep-0486/
[rsVna]: https://github.com/Terrabits/rohdeschwarz
[pyPackDep]: http://python-packaging.readthedocs.io/en/latest/dependencies.html
[fsPyAppDep]: https://www.fullstackpython.com/application-dependencies.html
[pipFreeze]: https://pip.pypa.io/en/stable/reference/pip_freeze/
[soVenvAss]: http://stackoverflow.com/questions/4879624/why-doesnt-virtualenv-on-windows-associate-py-pyw-pyo-pyc-files-with-virtua
[soVenvActivate]: http://stackoverflow.com/questions/4037939/powershell-says-execution-of-scripts-is-disabled-on-this-system
[soVenvActivate2]: http://stackoverflow.com/questions/14604699/how-to-activate-virtualenv
[gitIgnore]: https://help.github.com/articles/ignoring-files/
[enigmetaFlask]: http://www.enigmeta.com/blog/starting-flask/
[autoEnvWrapper]: http://timmyreilly.azurewebsites.net/python-pip-virtualenv-installation-on-windows/
[vEnvGit]: http://stackoverflow.com/questions/6590688/is-it-bad-to-have-my-virtualenv-directory-inside-my-git-repository
[gitTracked]: http://stackoverflow.com/questions/15606955/how-can-i-make-git-show-a-list-of-the-files-that-are-being-tracked
[venvToolsSummary]: http://stackoverflow.com/questions/41573587/what-is-the-difference-between-venv-pyvenv-pyenv-virtualenv-virtualenvwrappe
[flaskShell]: http://flask.pocoo.org/docs/0.12/cli/
[powershellCommands]: https://technet.microsoft.com/en-us/library/ff730964.
[virtualenvAtom]: https://atom.io/packages/virtualenv
[githubPush]: https://help.github.com/articles/adding-an-existing-project-to-github-using-the-command-line/