---
title: AddLinkedNodesToLinearSystem
category: moduledocs
tags: module

---

# AddLinkedNodesToLinearSystem

## Description

### Summary

This module will link nodes in a finite element mesh and solve them as a single value.

### Detailed Description

AddLinkedNodesToLinearSystem works with AddKnownsToLinearSystem and SolveLinearSystem to force nodes in a finite element mesh to solve to the same value. This module is useful in solving for regions with homogeneous field properties, such as with a perfect conductor in an electric field. The algorithm to do this involves combining rows in the stiffness matrix corresponding to the nodes to solve together. The module also creates a mapping matrix that will map the results of the solve linear system to the original mesh.

AddLinkedNodesToLinearSystem has three **inputs:** 

The first two are the matrix (A) and the right hand vector (b) for a linear system (Ax=b) and correspond to the two outputs of the AddKnownsToLinearSystem module. 

The third input is a matrix representing the data marking the nodes to link on the same mesh used in the [BuildFEMatrix](buildfematrix) module. The nodes should be marked with an integer value so that nodes to be linked will have the same value. Any number of linked node sets can be used by using a different value, i.e., independent sets of nodes to be linked must be marked 1,2,3 creating three regions of linked nodes. The remaining nodes should be marked NaN. This can be accomplished be using MapFieldDataOntoNodes and using the Default Outside Value of NaN and a Maximum Distance of some value that is small relative to your mesh size. Then use GetFieldData to port the matrix into AddLinkedNodesToLinearSystem.

There are three **outputs** of AddLinkedNodesToLinearSystem:

  * The first two are the reduced matrix (A) and right hand vector (b) for a linear system to use in SolveLinearSystems. 

  * The third is a mapping matrix to restore the data (solution vector from linear system solution) the proper size. To do this multiply the mapping matrix and the first output of SolveLinearSystem. The resulting vector can then be applied to the original mesh used in the calculation.