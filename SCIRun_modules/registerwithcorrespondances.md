---
title: RegisterWithCorrespondances
category: moduledocs
tags: module

---

#RegisterWithCorrespondances

##Description

###Summary

This module allows you to morph using a thin plate spline algorithm one point set or mesh to another point set or mesh. It also has the option for a rigid transformation. Both options require correspondence points from both point sets. This module also requires SCIRun to be compiled with LAPACK or Blas.

###Detailed Description

####Inputs

  1. **InputField:** This will read the node locations from an input mesh that is to be transformed.

  2. **Correspondences1:** This reads the node locations from a field of the correspondence points in the new coordinate system.

  3. **Correspondences2:** This reads the node locations from a field in the same coordinate system as the input field.
