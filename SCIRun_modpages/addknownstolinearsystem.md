---
title: AddKnownsToLinearSystem
category: moduledocs
tags: module

---

# AddKnownsToLinearSystem

## Description

### Summary

This module deals with solving a linear system A*u=b when some values of the vector u is already known. The module will modify the linear system according to the known values.

### Detailed Description

This module takes 3 inputs, denoted by A, b and x.

  1. A is an NxN matrix. A must be a SparseRowMatrix.
  2. b is the right hand side vector, an N*1 vector.
  3. x is an Nx1 vector specifying the known variables in the linear system A. If the kth variable is known, x(k) is its value, otherwise x(k) should be set NaN.
  
This module returns 2 outputs, denoted by A2 and b2. 

  1. A2 is an NxN matrix 
  2. b2 is an Nx1 vector. 
  
Their solution: 
```
inv(A2)*b2
```
has the same value as x at those non-NaN positions.
