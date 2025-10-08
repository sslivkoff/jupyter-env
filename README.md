
# Jupyter Env

This repo configures a reproducible jupyter lab environment using `uv`

## Commands

Initiation:
```bash
git clone https://github.com/sslivkoff/jupyter-env
cd jupyter-env
uv sync
```

Add to `~/.profile`:
```bash
# start jupyter lab server
alias j='uv run --project ~/repos/jupyter-env jupyter lab --notebook-dir="$HOME/notebooks"'

# start ipython session
alias i='uv run --project ~/repos/jupyter-env ipython'

# this allows python shebangs to use the jupyter-env python
# replace ~/repos/jupyter-env with the path to this repo
export PATH="$HOME/repos/jupyter-env/.venv/bin:$PATH"
```

Update dependencies
```bash
# check what can be updated
uv lock --upgrade --dry-run

# gather updates
uv lock --upgrade

# sync updates
uv sync
```

## Add extensions

view active extensions with `uv run jupyter labextension list`

```
uv run jupyter server extension enable jupyterlab_execute_time
```

#### Softlink jupyter extension settings

```bash
ln -s ./extension_settings/jupyterlab_code_formatter/ ~/.jupyter/lab/user-settings/
```

## Add rust kernel to jupyter

```bash
# install evcxr
cargo install evcxr_jupyter

# activate venv and install evcxr kernel
source .venv/bin/activate
evcxr_jupyter --install

# validate kernel is installed
jupyter kernelspec list
```
