# sat_velocity_processor
## Interpolate, smooth, and otherwise process gappy, discontinuous, and unevenly sampled glacier velocities

The main notebook here `vel_fields.ipynb`, reads in a set of velocity geotiffs (just the x velocities at this point), 
identifies the mean velocity among these geotiffs and the anomalies from that mean velocity, and then identifies 
the dominant modes of variability among those velocity fields.  Dominant modes of variability are distinguished as
a set of empirical orthogonal functions (EOFs), and each velocity field from each date is decomposed into these dominant
modes.

The identified EOFs and their eigenvalues (constituent contributions) are then used to reconstruct the velocity fields
and infer the likely values of missing data.  This iterative process of decomposition and reconstruction produces 
complete, filled, uniform velocity fields, without any gaps.

After complete, continuous velocity fields are estimated, the notebook smooths the velocity fields and assesses the
temporal variability of glacier velocities.

This analysis was initiated in March 2022 for research led by Dakota Pyles, which uses the mass continuity equation to estimate
glacier ablation.

This notebook draws on the modules `rasterio` and `eofs`, both of which are present within the UI Glacier Dynamics
environment `spatialenv22a`, created from `spatialenv.yml`.
