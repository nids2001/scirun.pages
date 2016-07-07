---
title: RefineTetMeshLocally
category: moduledocs
tags: module

---

#RefineTetMeshLocally

##Description

###Summary

This module tidies up node orientation and removes degenerate tetrahedral elements on a given tetrahedral mesh.

###Detailed Description

This module performs two cleanup tasks on a given tetrahedral mesh:

  1. Fix the node orientation in each tetrahedral element.
  2. Removing degenerate tetrahedral elements. 
  
Both tasks can be selected in the UI.

The input field must be a tetrahedral mesh, otherwise the module will do nothing and return an error. The module outputs the processed mesh.