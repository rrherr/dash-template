# dash-template

- [First time](#first-time)
  - [Requirements](#requirements)
  - [Setup](#setup)
- [Every time](#every-time)
  - [Change directory into the repo](#change-directory-into-the-repo)
  - [Activate the Pipenv shell](#activate-the-pipenv-shell)
- [How to](#how-to)
  - [Run the app](#run-the-app)
  - [Launch Jupyter Notebook](#launch-jupyter-notebook)
  - [Exit the Pipenv shell](#exit-the-pipenv-shell)
  
## First time

### Requirements
You need this software on your local computer:

- A **terminal**. If you're on Windows, I recommend [Git Bash](https://gitforwindows.org/).
- **Python 3**. I recommend [Anaconda Distribution](https://www.anaconda.com/distribution/).
- An **IDE** (Integrated Development Environment) or text editor. I recommend [VS Code](https://code.visualstudio.com/).

You also need to install [**Pipenv**](https://pipenv.readthedocs.io/en/latest/).

```
pip install pipenv
```

> It automatically creates and manages a virtualenv for your projects, as well as adds/removes packages from your Pipfile as you install/uninstall packages. It also generates the ever-important Pipfile.lock, which is used to produce deterministic builds.

### Setup

[Create a new repository from this template](https://github.com/rrherr/dash-template/generate).

Clone the repo onto your local computer:
```
git clone https://github.com/<you>/<repo>.git
```

Change directory into the repo:
```
cd <repo>
```

Create a virtual environment for this project, and install dependencies from Pipfile.lock:
```
pipenv install
```

Next, [activate the Pipenv shell](#activate-the-pipenv-shell) & [run the app](#run-the-app)!

## Every time

### Change directory into the repo
```
cd <repo>
```

### Activate the Pipenv shell
```
pipenv shell
```

You can verify your virtual environment is active:

1. Look at your command prompt prefix
2. Run the command `which jupyter`

✅ You should see this:
```
(your-repo-name) $ which jupyter
/Users/you/.local/share/virtualenvs/your-repo-name/bin/jupyter
```

❌ Not this:
```
(base) $ which jupyter
/anaconda3/bin/jupyter
```

## How to

### Run the app
```
python run.py
```

Then in your browser, go to http://localhost:8050/

### Launch Jupyter Notebook
```
jupyter notebook
```

### Exit the Pipenv shell
```
exit
```






