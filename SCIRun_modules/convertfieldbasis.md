---
title: ConvertFieldBasis
category: moduledocs
tags: module

---

#ConvertFieldBasis

##Description

###Summary

ConvertFieldBasis can modify the location of data in the input field.

###Detailed Description

Upon execution the UI will display the input field name and the current location the data values for the that field are located.

The output field's new data value location is selected from a list of available basis types. The output field will contain the same geometry as the input field with the data value storage at the newly specified location. All output data values are reset to 0.

There is currently support for three basis functions within SCIRun. The first is None, meaning that there is no data associated with the field and that no interpolation is supported. The Constant basis is when data is associated with the elements of a field. This data is not interpolated but is constant within each element and non-continuous at element boundaries. The third basis function is Linear. Linear means that the data is associated with the nodes of a field. Any interpolation will be done linearly within elements (but not across element boundaries).