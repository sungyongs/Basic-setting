# Basic-setting
Basic settings about conda, jupyter, tensorflow, or other settings.


## Conda
[Conda Manual](https://conda.io/docs/index.html)
- See environments list
  - `conda info --envs`
- Create new environments
  - Python 3.5, `conda create --name py35 python=3.5 [other packages]`
  - Python 2.7, `conda create --name py27 python=2.7 [other packages]`
- Create new environments with ipykernel (__Recommended__)
  - `conda create -n py35 python=3.5 ipykernel`

If `ipykernel` is installed in other environments, we can load the `ipykernel` in main `jupyter-notebook`. It is unnecessary to install `jupyter-notebook` or other packages for `jupyter-notebook`. 

- Switch environments
  - `source activate py35`
  - `source deactivate`
- Path of kernels
  - `~/anaconda2/envs/[env_name]/share/jupyter/kernels/[kernel-name]`

[__Note__] If a package is NOT installed in an active environment but the conda-root, the package is not imported.
For example, `numpy` is only installed in the `conda-root`. (not installed in `py35`)
```
source activate py35
python
import numpy
ImportError: No module named 'numpy'
```
