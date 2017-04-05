# Basic-setting
Basic settings about conda, jupyter, tensorflow, or other issues


## Conda
[Conda Manual](https://conda.io/docs/index.html)
- See environments list
`conda info --envs`
- Create new environments
  - Python 3.5, `conda create --name py35 python=3.5 [other packages]`
  - Python 2.7, `conda create --name py27 python=2.7 [other packages]`
- Create new environments with ipykernel
  - `conda create -n py35 python=3.5 ipykernel`
If `ipykernel` is installed in other environments, we can load the `ipykernel` in main `jupyter-notebook`.
It is unnecessary to install `jupyter-notebook` or other packages for `jupyter-notebook`. 
