---
title: SetFieldData
category: moduledocs
tags: module

---

#SetFieldData

##Description

###Summary

This module allows you to set the scalar, vector, or tensor entries of an array or single column matrix to the nodes or elements of a mesh. The module checks the size of the array and compares it to the number of elements and nodes in order to determine where to put the data. The first entry in the array is applied to the first location on the mesh and this continues sequentially.

###Detailed Description

####Inputs

  1. takes a field and it expects a mesh or a point set

  2. takes an array of data or matrix

  3. takes NRRD data: this can be used instead in place of the matrix.