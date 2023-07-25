# geodesic

A series of utilities to compute geodesic calculations.

## list of methods

The code implements the Vincenty's formulas to solve the direct and incverse geodesic problem.
The CPU code is implemented in python using numba, while the GPU code is implemented in cupy and cudf.

### CPU

* calculateRangeBearingFromGeographicals()
* calculateGeographicalPositionFromRangeBearing()

### GPU

* calculateGeographicalPositionFromRangeBearing()

---

CPU code for single point is much faster than GPU code. However, GPU code is much faster for batch of large dataset and offer convenient support to work with dataframes. CPU code address both direct and inverse geodesic problems and has a speed-up of over 10x comapred with the analogous code in the geographiclib library.

The `calculateGeographicalPositionFromRangeBearing()` method is used in combination with a multivariate regression model to derive the position of a towed camera. The camera position [destination point] is computed from a given a starting point [vessel position], a bearing [vessel heading] and a distance (predicted) [layback distance]. The prediction is computed from: camera depth, vessel speed, camera distance from seafloor, etc ..], see [layback_modeling](http://github.com/epifanio/layback_modeling) for more details.
