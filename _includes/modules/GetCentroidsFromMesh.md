---
title: GetCentroidsFromMesh
category: moduledocs
module:
  category: NewField
  package: SCIRun
tags: module

---

# {{ page.title }}

## Category

**{{ page.module.category }}**

## Description

### Summary

Computes a PointCloudField containing all of the elements for a field.
**Detailed Description**

The Centroids module computes a PointCloudField containing all the element /node/face/edge/cell/delement centers for a field. For instance, if the input field is a TetVolField then the output field would contain the center of each tetrahedra. An input PointCloudField would return the same data locations.

The output field is always a PointCloudField of doubles, and contains no data. If data is needed at the points then an interpolation module should be used to recover them.

{% capture url %}{% include url.md %}{% endcapture %}
{{ url }}
