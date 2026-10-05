# MSc Project: Dust Substructure in Ophiuchus Protoplanetary Discs

> **Note:** This repository is a code showcase. The ALMA data is not
> included, so the notebooks are not runnable as-is.

## Overview
Analysis of ALMA Band 6 continuum observations of protoplanetary discs
in the Ophiuchus Molecular Cloud (ODISEA survey), carried out as part of
my MSc in Astrophysics at Queen Mary University of London. The code fits
axisymmetric models to each disc and examines the residuals for
non-axisymmetric substructure.

## Pipeline
1. Image processing in CASA ([tclean / exportfits])
2. Axisymmetric visibility modelling with frank, producing radial
   brightness profiles.
3. Unit conversion and smoothing of the model image to match the
   observation (Jy/sr to Jy/beam)
4. Reprojection and subtraction in Astropy to produce residual maps
5. Inspection of residuals for non-axisymmetric structure

## Repository contents
`MSc_project_code/` contains one notebook per source. Each notebook
applies the same pipeline to a single disc, named by source number
(e.g. `026_finalv2.ipynb`). '003_test_(use_this_one) serves as the 
reference case: it documents the parameter and
shift tests that informed the final pipeline settings. 


## Notes on methods
- Centroid offsets were handled with frank's `phase_shift=True`
  option rather than editing image headers.
- A half-pixel offset (`half_px = 0.5`) is applied when aligning the
  model image with the observed image / converting between pixel
  coordinate conventions, so that the residual maps are centred
  correctly.

## Dependencies
Python 3.11, frank, Astropy, NumPy, Matplotlib, CASA 
