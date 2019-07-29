# dash-template

- [First time](#first-time)
  - [Requirements](#requirements)
  - [Setup](#setup)
- [Every time](#every-time)
  - [Change directory into the repo](#change-directory-into-the-repo)
  - [Activate the Pipenv shell](#activate-the-pipenv-shell)
- [How to](#how-to)
  - [Run the app](#run-the-app)
  - [See installed packages](#see-installed-packages)
  - [Install packages](#install-packages)
  - [Launch Jupyter Notebook](#launch-jupyter-notebook)
  - [Change the app name in the browser title bar](#change-the-app-name-in-the-browser-title-bar)
  - [Change the app name in the navigation bar](#change-the-app-name-in-the-navigation-bar)
  - [Change your name and contact info in the footer](#change-your-name-and-contact-info-in-the-footer)
  - [Change Bootswatch theme](#change-bootswatch-theme)
  - [Change navigation bar colors](#change-navigation-bar-colors)
  - [Change home page text & button](#change-home-page-text--button)
  - [Exit the Pipenv shell](#exit-the-pipenv-shell)
  
## First time

### Requirements
You need this software on your local computer:

- A **terminal**. If you're on Windows, I recommend [Git Bash](https://gitforwindows.org/). If you're on Mac or Linux, a terminal is built in.
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

Ctrl+C quits the app.

### See installed packages
```
cat Procfile
```

You'll see output like this:
```
[[source]]
name = "pypi"
url = "https://pypi.org/simple"
verify_ssl = true

[dev-packages]

[packages]
dash = "*"
dash-bootstrap-components = "*"
gunicorn = "*"
plotly = "*"
jupyter = "*"
pandas = "*"

[requires]
python_version = "3.7"
```

### Install packages
```
pipenv install <package>
```

For example, to install scikit-learn, category_encoders, xgboost, & [Dash DAQ](https://dash.plot.ly/dash-daq):
```
pipenv install scikit-learn category_encoders xgboost dash_daq
```

### Launch Jupyter Notebook
First, don't forget to [activate the Pipenv shell](#activate-the-pipenv-shell). Then:
```
jupyter notebook
```

### Change the app name in the browser title bar

Edit `app.py` file, `app.title` string:

```python
app.title = 'YOUR APP NAME' # appears in browser title bar
```

### Change the app name in the navigation bar

Edit `run.py` file, `navbar` object, `brand` string:

```python
navbar = dbc.NavbarSimple(
    brand='YOUR APP NAME',
    ...
)
```

### Change your name and contact info in the footer

Edit `run.py` file, `footer` object:

```python
footer = dbc.Container(
    dbc.Row(
        dbc.Col(
            html.P(
                [
                    html.Span('Your Name', className='mr-2'), 
                    html.A(html.I(className='fas fa-envelope-square mr-1'), href='mailto:<you>@<provider>.com'), 
                    html.A(html.I(className='fab fa-github-square mr-1'), href='https://github.com/<you>/<repo>'), 
                    html.A(html.I(className='fab fa-linkedin mr-1'), href='https://www.linkedin.com/in/<you>/'), 
                    html.A(html.I(className='fab fa-twitter-square mr-1'), href='https://twitter.com/<you>'), 
                ], 
                className='lead'
            )
        )
    )
)
```

### Change Bootswatch theme

Browse themes at https://bootswatch.com/

- `dbc.themes.BOOTSTRAP`
- `dbc.themes.CERULEAN`
- `dbc.themes.COSMO`
- `dbc.themes.CYBORG`
- `dbc.themes.DARKLY`
- `dbc.themes.FLATLY`
- `dbc.themes.JOURNAL`
- `dbc.themes.LITERA`
- `dbc.themes.LUMEN`
- `dbc.themes.LUX`
- `dbc.themes.MATERIA`
- `dbc.themes.MINTY`
- `dbc.themes.PULSE`
- `dbc.themes.SANDSTONE`
- `dbc.themes.SIMPLEX`
- `dbc.themes.SKETCHY`
- `dbc.themes.SLATE`
- `dbc.themes.SOLAR`
- `dbc.themes.SPACELAB`
- `dbc.themes.SUPERHERO`
- `dbc.themes.UNITED`
- `dbc.themes.YETI`

Edit `app.py` file, `external_stylesheets` parameter:

```python
external_stylesheets = [
    dbc.themes.BOOTSTRAP, # Bootswatch theme
    'https://use.fontawesome.com/releases/v5.9.0/css/all.css', # for social media icons
]

app = dash.Dash(__name__, external_stylesheets=external_stylesheets)
```

### Change navigation bar colors

First, choose your [Bootswatch theme](#change-bootswatch-theme).

Then, edit `run.py` file, `navbar` object, `color`, `light` & `dark` parameters:

```python
navbar = dbc.NavbarSimple(
    ...
    color='light', 
    light=True, 
    dark=False
)
```

These parameters are explained in [Dash Bootstrap Components docs](https://dash-bootstrap-components.opensource.faculty.ai/l/components/navbar):

> `color` _(string, optional)_: Sets the color of the NavbarSimple. Main options are primary, light and dark, default light. You can also choose one of the other contextual classes provided by Bootstrap (secondary, success, warning, danger, info, white) or any valid CSS color of your choice (e.g. a hex code, a decimal code or a CSS color name)

> `light` _(boolean, optional)_: Applies the `navbar-light` class to the NavbarSimple, causing text in the children of the Navbar to use dark colors for contrast / visibility.

> `dark` _(boolean, optional)_: Applies the `navbar-dark` class to the NavbarSimple, causing text in the children of the Navbar to use light colors for contrast / visibility.

### Change home page text & button

Edit `pages/index.py` file, `column1` object:

```python
column1 = dbc.Col(
    [
        dcc.Markdown(
            """
        
            ## Value Proposition

            Emphasize how the app will benefit users. Don't emphasize the underlying technology.

            ✅ RUN is a running app that adapts to your fitness levels and designs personalized workouts to help you improve your running.

            ❌ RUN is the only intelligent running app that uses sophisticated deep neural net machine learning to make your run smarter because we believe in ML driven workouts.

            """
        ),
        dcc.Link(dbc.Button('Call To Action', color='primary'), href='/predictions')
    ],
    md=4,
)
```

#### Docs
- [`dbc.Col`](https://dash-bootstrap-components.opensource.faculty.ai/l/components/layout)
- [`dcc.Markdown`](https://dash.plot.ly/dash-core-components/markdown)
- [`dcc.Link`](https://dash.plot.ly/urls)
- [`dbc.Button`](https://dash-bootstrap-components.opensource.faculty.ai/l/components/button)

The RUN app example comes from [Google's People + AI Guidebook](https://pair.withgoogle.com/chapter/mental-models/).

### Exit the Pipenv shell
```
exit
```
