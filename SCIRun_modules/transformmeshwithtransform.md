---
title: TransformMeshWithTransform
category: moduledocs
tags: module

---

#TransformMeshWithTransform

##Description

###Summary

This module performs a non-interactive geometric transform of a field.

###Detailed Description

This module is used to non-interactively transform the geometry of a field. The transform is passed in to the **Transform Matrix** port as a 4x4 matrix. There is no GUI for this module. The transform is generally computed by a different module, such as [AlignMeshBoundingBoxes](alignmeshboundingbox). For interactive geometry transforms, use the [CreateGeometricTransform](creategeometrictransform) module.

Note that for fields containing vectors and tensors, the direction of the data will be **altered** by the transform.