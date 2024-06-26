The module `csp.random` contains a few nodes (contributions welcome) to help simulate stochastic processes to assist with testing, examples and demos.

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Arrival Processes](#arrival-processes)
- [Random Noise](#random-noise)
- [Diffusion Processes](#diffusion-processes)

## Arrival Processes

These nodes extend the deterministic `csp.timer` node with other arrival processes for triggering events.

```python
csp.random.poisson_timer(
    rate: ts[float],
    seed: object,
    value: "~T" = True
) -> ts["T"]
```

Generate events according to a Poisson process with time-varying rate. For a fixed-interval timer see `csp.timer`.

Args:

- **`rate`**: The rate of the Poisson process (per second), must be non-negative
- **`seed`**: The seed for the numpy random Generator. Can be anything accepted by `np.random.default_rng`
- **`value`**: The value to tick when there are events (similar to `csp.timer`)

## Random Noise

To generate random noise at trigger times, the `csp.apply` node can be used. For example, to generate random samples at the tick times of a `trigger` edge following a Laplace distribution:

```python
import csp
import numpy as np
from csp.typing import Numpy1DArray

rng = np.random.default_rng()

random_noise_1d = csp.apply(
    trigger,
    lambda _: rng.laplace(0, 1),
    result_type=float
)

random_noise = csp.apply(
    trigger,
    lambda _: rng.laplace(0, 1, size=10),
    result_type=Numpy1DArray[float]
)
```

See the [Numpy Random Generator documentation](https://numpy.org/doc/stable/reference/random/generator.html#distributions) for a full list of distributions.

## Diffusion Processes

These nodes simulate samples from diffusion processes at a provided set of trigger events.

```python
csp.random.brownian_motion(
    trigger: ts[object],
    drift: ts[Numpy1DArray[float]],
    covariance: ts[NumpyNDArray[float]],
    seed: object,
    return_increments: bool = False
) -> ts[Numpy1DArray[float]]:
```

Generate multi-dimensional Brownian motion (or increments) at the trigger times, with time-varying drift and covariance.
The Brownian motion starts once drift and covariance have at least 1 tick each, and will start from zero.
To use a different start value, use `csp.const(initial_value) + brownian_motion(...)`

Args:

- **`trigger`**: When to return the value of the process
- **`drift`**: Drift parameter (per second), i.e. array of length n
- **`covariance`**: Covariance matrix (per second), i.e. array of size nxn
- **`seed`**: The seed for the numpy random Generator. Can be anything accepted by `np.random.default_rng`
- **`return_increments`**: Whether to return increments of the brownian motion at trigger times instead of the process itself

```python
csp.random.brownian_motion_1d(
    trigger: ts[object],
    drift: ts[float],
    covariance: ts[float],
    seed: object,
    return_increments: bool = False
) -> ts[float]:
```

Generate one-dimensional Brownian motion at the trigger times, with time-varying drift and variance.
The Brownian motion starts once drift and variance have at least 1 tick each, and will start from zero.
To use a different start value, use `csp.const(initial_value) + brownian_motion_1d(...)`

- **`trigger`**: When to return the value of the process
- **`drift`**: Drift parameter (per second)
- **`covariance`**: Variance parameter (per second)
- **`seed`**: The seed for the numpy random Generator. Can be anything accepted by `np.random.default_rng`
- **`return_increments`**: Whether to return increments of the brownian motion at trigger times instead of the process itself
