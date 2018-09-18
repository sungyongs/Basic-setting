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
  - Consider following packages when above command is used:
    - (Basic) pandas, scipy, matplotlib
    - (Deep learning) tensorflow [See intall guide](https://www.tensorflow.org/install/)
    - (Network) networkx

If `ipykernel` is installed in other environments, we can load the `ipykernel` in main `jupyter-notebook`. It is unnecessary to install `jupyter-notebook` or other packages for `jupyter-notebook`. 

[__Note__] Since `jupyter lab` is launched, `nb_conda_kernel` should be installed to load the kernels in other environments. Do the following command in the **base** environment.
```python
[Deprecated]conda install -c conda-forge nb_conda_kernels
conda install nb_conda_kernels
```
[__Note__] If a following error appears,
```bash
undefined symbol: zmq_curve_public
```
Reinstall `pyzmq` and `zmq`.
```bash
$ pip install pyzmq
$ pip install pyzmp --upgrade
```

Then, it should be able to load other kernels. [See issue](https://github.com/jupyterlab/jupyterlab/issues/1557).

- Switch environments
  - `source activate py35`
  - `source deactivate`
- Path of kernels
  - `~/anaconda2/envs/[env_name]/share/jupyter/kernels/[kernel-name]`

[__Note__] If a package is NOT installed in an active environment but the conda-root, the package is not imported.
For example, `numpy` is only installed in the `conda-root`. (not installed in `py35`)
```python
source activate py35
python
import numpy
ImportError: No module named 'numpy'
```

## SSH login with (authentication) key

Objectives:

* Set up password-less SSH login

Benefits:

* Easier to login

Let's begin.

1. On **local** machine, create an authentication key-pair *if you don't have one*. Don't enter the passphrase if you don't want to use it

    ```bash
    ssh-keygen -t rsa -b 2048 -f id_rsa
    ```

2. Add your key to **local** authentication agent

    ```bash
    ssh-add ~/.ssh/id_rsa
    ```

3. Copy your key from *local* machine to the *server*

    ```bash
    scp ~/.ssh/id_rsa.pub {**SERVER**}:~
    ```

4. On the **server**, Add your key to the list of authorized keys

    ```bash
    cd ~/.ssh
    cat ~/id_rsa.pub >> authorized_keys2
    rm ~/id_rsa.pub
    ```

