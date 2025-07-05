
# Jupyter Env

## Jupyterlab extensions

view active extensions with `uv run jupyter labextension list`

```
uv run jupyter server extension enable jupyterlab_execute_time
```

## Add rust kernel

```bash
# install evcxr
cargo install evcxr_jupyter

# activate venv and install evcxr kernel
source .venv/bin/activate
evcxr_jupyter --install

# validate kernel is installed
jupyter kernelspec list
```
