# genericFlaskEnv
Exercise of setting up a python virtualEnv and flask and a repository. The
packages are all used in the [flask mega tutorials][flaskTutorial]. Below 
is a short description of the setup. For more notes check out the notes.md
file. It has information and reference links for information on setting up
a virtualenv, especially on windows using powershell mostly.

## Setup
This requires a local python version and virtualenv. The below instructions
work using powershell on windows. Tested with python 3.5.2 anaconda version.

* git clone https://github.com/rschutjens/genericFlaskEnv.git
* cd genericflaskEnv
* virtualenv flask
* .\flask\Scripts\activate
* pip install -r requirements.txt
* python run.py
* open a browser and go to http://127.0.0.1:5000/

[flaskTutorial]: https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world
