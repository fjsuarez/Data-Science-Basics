# Getting started

## Set up

### Check `python`

```bash
python --version
```

### Check `conda` environment

```bash
conda list
```

### Update `conda` or all packages

```bash
conda upgrade conda
conda upgrade --all
```

### Install a new package

```bash
conda install numpy
```

Or an specific version

```bash
conda install numpy=1.10
```

### Remove a package

```bash
conda remove numpy
```

### Search for a package

Make use of wildcards

```bash
conda search *beautifulsoup*
```

### Install Jupyter Notebook

```bash
conda install jupyter notebook
```

### Launch Jupyter Notebook

```bash
jupyter notebook
```

### Install Notebook Conda

This is helpful to manage environments from Jupyter Notebook

```bash
conda install nb_conda
```

## Using Jupyter Notebook

### Magic Keywords

[Magic Keywords documentation](http://ipython.readthedocs.io/en/stable/interactive/magics.html)

#### `%matplotlib`

Use it to set up matplotlib from your notebook. For example, you can use Inline backend, and render images for retina resolution:

```python
%matplotlib inline
config InlineBackend.figure_format = 'retina'
```

#### `%pdb`

Use it for debugging. Type `q` on the prompt to leave the debugger.

#### `%timeit`

Use it for timing instructions in a cell.

### Converting Notebooks

You can convert notebooks to multiple formats with `nbconvert`:

```bash
jupyter nbconvert --to html notebook.ipynb
```

You can convert them to slides and serve them:

```bash
jupyter nbconvert notebook.ipynb --to slides --post serve
```