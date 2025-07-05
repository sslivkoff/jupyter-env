
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
alias uvjl='uv run --project ~/repos/jupyter-env jupyter lab --notebook-dir="$HOME/notebooks"'

# start ipython session
alias i='uv run --project ~/repos/jupyter-env ipython'
```

## Add extensions

view active extensions with `uv run jupyter labextension list`

```
uv run jupyter server extension enable jupyterlab_execute_time
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
