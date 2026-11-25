# Periodogram, Bartlett and Welch

A Jupyter notebook that works through power spectral density estimation from first principles.
It proves the bias of the periodogram (the Fejér kernel) and its variance, which shows why more
data never makes it consistent, and then derives Bartlett's and Welch's methods, including Welch's
normalization factor and the variance of overlapping segments. Each proof is followed by a code
cell that checks it numerically. The notebook ends with a Monte Carlo comparison of bias,
variance and MSE, and a check of `scipy.signal` against code written from scratch.

Everything is in [periodogram.ipynb](periodogram.ipynb). Its 26 figures are saved in the file,
so you can read it without running anything.

## Running it

You need Python 3.12 or later and [uv](https://docs.astral.sh/uv/).

```bash
uv run jupyter lab periodogram.ipynb                                          # open it
uv run jupyter nbconvert --to notebook --execute --inplace periodogram.ipynb  # re-run every cell
```

The notebook uses NumPy, SciPy and Matplotlib on synthetic signals with a fixed random seed, so a
re-run prints the same numbers. A full run takes about 15 seconds.
