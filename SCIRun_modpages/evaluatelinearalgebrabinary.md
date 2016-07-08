---
title: EvaluateLinearAlgebraBinary
category: moduledocs
tags: module

---

# EvaluateLinearAlgebraBinary

## Description

### Summary

This module performs one of a number of selectable matrix operations using the two input matrices.

### Detailed Description

One of a number of binary matrix operations can be selected from the GUI and is then applied to the two input matrices to produce a new matrix that is then sent to the output port. The operations are X, +, Normalize, Select Rows, Select Columns, or Function.

**"A X B"** does a matrix multiply of the two matrices. The number of rows in the first matrix must match the number of columns in the second matrix. The output matrix has the same number of columns as the first matrix and the same number of rows as the second.

**"A + B"** performs a matrix addition. The two input matrices must be the same size. The elements are added in a piecewise fashion. This is equivalent to selecting "Function" and using 'x+y' as the function description

**"Normalize A to B"** computes the min and max values of the second matrix, and then linearly transforms all of the elements in the first matrix so that they fall within the range of those min and max values.

**"Select Rows"** uses the values in the B input matrix as row indices to extract from the A input matrix. The B input matrix must be a Column Matrix containing valid row index values into the A matrix. For example, if the B matrix contains [3 5] and the A matrix is 100x200, then the resulting matrix will be 2x200 and contain rows 3 and 5 from the A matrix.

**"Select Columns"** uses the values in the B input matrix as column indices to extract from the A input matrix. The B input matrix must be a ColumnMatrix containing the valid column index values into the A matrix. For example, if the B matrix contained [3 5] and the A matrix is 100x200, then the resulting matrix will be 100x2 and contain columns 3 and 5 from the A matrix.

**"Function"** allows an arbitrary function of two variables to be evaluated for each number pair in the two input matrices. This requires that the two matrices are the same size. The variable representing the element from the A matrix is 'x', and the variable for the element from the B matrix is 'y'. The function is specified using SCIRun's simple function parser. There are a number of mathematical functions available for use. They are:

**Operators:**

  * +: Add two numbers: 
<pre>
4+3 = 7
</pre>

  * -: Subtract one number from another: 
<pre> 
4-3 = 1 
</pre>

  * Multiply two numbers.: <pre> 4*3 = 12 </pre>

  * Divide one number from another: <pre>12/3 = 4</pre>

  * sin: Sine of a number in **radians**: <pre>sin(x)</pre>

  * cos: Cosine of a number in **radians**: <pre>cos(x)</pre>

  * sqrt: Square root of a number: <pre>sqrt(4) = 2</pre>

  * sqr: Square of a number: <pre>sqr(2) = 4</pre>

  * ln: Natural logarithm of a number: <pre>ln(x)</pre>

  * exp: e raised to the nth power. <pre>exp(ln(x)) = x</pre>

  * log: Log base 10 of a number: <pre>log(100) = 2</pre>

  * abs: Absolute value of a number: <pre>abs(-3) = 3</pre>

  * pow: One number raised to the power of another: <pre>pow(3, 2) = 9</pre>

  * random: Return a uniform random number between 0 and 1: <pre>random()</pre>

