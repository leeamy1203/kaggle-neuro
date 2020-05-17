# Kaggle TReNDS Neuroimaging

This repo explores a Kaggle competition called [TReNDS Neuroimaging](https://www.kaggle.com/c/trends-assessment-prediction/overview/description)
We will be predicting multiple assessments (as well as age) from multimodal brian MRI features.

Go to the [wiki](https://github.com/leeamy1203/kaggle-neuro) for more details on the problem set and modeling work.

## Setup

### Tooling

- Install Python, minimum 3.7.5 ([pyenv](https://github.com/pyenv/pyenv) is the easiest way to install specific versions)
- Python Environment/Dependency Management via [poetry](https://python-poetry.org/) 
  - Install poetry - [instructions](https://python-poetry.org/docs/#installation)
- DVC for Data Pipeline Management
  - Install dvc - [instructions](https://dvc.org/doc/install/macos)
- Jupyter Notebook environment via Docker

A lot of opinions were pulled from [here](https://drivendata.github.io/cookiecutter-data-science/#directory-structure)


## General Usage

Because of the repository structure and poetry for dependency management, you can leverage auto-completion within the 
IDE and leverage that same code within the Jupyter Notebooks. In addition, the python packages you pull in will be the
same versions between your IDE and the Jupyter Notebook.

### Configure IDE for Usage

If using PyCharm, you'll need to set the project interpreter as the virtualenv that was created when getting 
dependencies installed. To do this, run `poetry env list --full-path` to get the full directory path of the 
Python environment.

### Configure Jupyter Notebook

Navigate into the root of the cloned directory, and run `docker-compose up` to launch a Jupyter Notebook server. If you
change any dependencies through poetry, you'll need to rebuild the container via `docker-compose build`. 

Note that the Jupyter notebook by default sets the root to be the repository root, so all files that are used for notebook
development should be within the repository. 

If you'd like to have a different port for your Jupyter server, you can run `JUPYTER_PORT=<new port> docker-compose up`
to use whatever port you'd like. The default messaging will still say port 8888, but it's allocated to whatever port
you pass in.

#### Use `src` in notebooks

Leverage the following code snippet to use the `src` directory in notebooks

```python
import sys
# This should navigate to the repository root
sys.path.append('../')

%reload_ext autoreload
%autoreload 2
```
