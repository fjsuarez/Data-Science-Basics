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

### Reading and loading data

#### Using `numpy`

```python
numpy.loadtxt('data.csv', delimiter = ',')
```

#### Using `pandas`

```python
pandas.read_csv('data.csv')
```

Assigning specific columns to variables

```python
X = data.iloc[:,:-1]
y = data.iloc[:,-1]
```

Remove column from dataframe

```python
data.drop('Header', axis = 1)
```

Combining `pandas` and `numpy`

```python
data = numpy.asarray(pandas.read_csv('data.csv', header=None))
```

### Linear Regression

#### Simple Linear Regression

```python
from sklearn.linear_model import LinearRegression
model = LinearRegression()
model.fit(X, y)
model.predict(X_test)
```

#### Polynomial Regression

```python
from sklearn.preprocessing import PolynomialFeatures
from sklearn.linear_model import LinearRegression

poly_feat = PolynomialFeatures(degree = 4)
X_poly = poly_feat.fit_transform(X)
poly_model = LinearRegression(fit_intercept = False).fit(X_poly, y)
model.predict(X_test)
```

#### Using `pipeline`

```python
from sklearn.preprocessing import PolynomialFeatures
from sklearn.linear_model import LinearRegression
from sklearn.pipeline import make_pipeline

poly_model = make_pipeline(PolynomialFeatures(degree=4), LinearRegression())
poly_model.fit(X, y)
model.predict(X_test)
```

### Linearization

#### L1 Linearization (Lasso)

```python
from sklearn.linear_model import Lasso

lasso_reg = Lasso()
lasso_reg.fit(X,y)
reg_coef = lasso_reg.coef_
```

For L2 linearization, `Ridge` can be used

### Feature Scaling

#### Standard Scale

```python
from sklearn.linear_model import Lasso
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()

X_scaled = scaler.fit_transform(X)
lasso_reg = Lasso()
lasso_reg.fit(X_scaled, y)
reg_coef = lasso_reg.coef_
```