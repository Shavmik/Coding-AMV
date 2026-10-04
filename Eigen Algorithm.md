## [**GitHub @Shavmik**](https://github.com/Shavmik)

## [**Insta @Shavmik**](https://www.instagram.com/shavmik/)

## [**YouTube @Shavmik**](https://www.youtube.com/@Shavmik)

# **Alogrithm :**

Step 1: Start

Step 2: Create a class named Eigen

Step 3: Declare a 2D array matrix of size 3X3 of type double and instantiate a Scanner object sc to read user input

Step 4: Define the default constructor Eigen() to get and store matrix.length

Step 5: Define the method accept():

Print "Please enter the elements of the 3X3 matrix row by row"

Run nested loops for i from 0 to 2 and j from 0 to 2 to read elements using sc.nextDouble() and store them in matrix\[i]\[j]

Print "\*All the inputs by the user are complete"

Step 6: Define the method checkUT() to check for an upper-triangular matrix:

Run nested loops for i from 0 to 2 and j from 0 to i - 1

If matrix\[i]\[j] != 0.0, print "Matrix doesnt fall under UT exception moving onto the real calculations" and return false

If upper-triangular condition holds, assign diagonal elements EV1 = matrix\[0]\[0], EV2 = matrix\[1]\[1], EV3 = matrix\[2]\[2]

Print "Matrix falls under UT exception" and print the three Eigen Values, then return true

Step 7: Define the method EigenValues(double\[]\[] matrix):

Call checkUT(); if it returns true, return an array containing { matrix\[0]\[0], matrix\[1]\[1], matrix\[2]\[2] }

Calculate Trace Tr as the sum of main diagonal elements: matrix\[0]\[0] + matrix\[1]\[1] + matrix\[2]\[2]

Calculate minors M11, M22, and M33 using standard 2x2 determinant formulas

Calculate coefficient coeff = M11 + M22 + M33 and determinant det of the 3x3 matrix

Set cubic equation coefficients a = -Tr, b = coeff, and c = -det

Compute intermediate variables p, q, and discriminant Discrim

Step 8: Handle discriminant cases for eigenvalues:

If Discrim > 0: Compute real and complex components using cube roots and square roots, store the single real eigenvalue in EV\[0], print that only one real eigenvalue exists, and return EV

Else if Math.abs(Discrim) < 1e-10: Compute repeating roots configuration using u and assign values to EV\[0], EV\[1], and EV\[2]

Else: Compute three real distinct roots using trigonometric formulas involving r and theta, and assign them to EV\[0], EV\[1], and EV\[2]

Print all calculated Eigen Values and return array EVStep 9: Define the method EigenVectors(double\[]\[] matrix, double\[] EV):

Initialize a 2D array vectors of size 3X3

Loop n from 0 to 2 for each eigenvalue lambda = EV\[n]

Construct matrix B = matrix - lambda \* I by subtracting lambda from the diagonal elements

Compute cross-product-like components x1, x2, and x3 from the first two rows of matrix B

If x1, x2, and x3 are approximately zero (< 1e-10), recompute components using the lower rows of B

Store x1, x2, x3 into vectors\[n] row

Print the Eigen Vectors mapped to their respective Eigen Values and return vectors

Step 10: Define the method display():

Call EigenValues(matrix) and store the result in EV array

Call EigenVectors(matrix, EV)

Step 11: Define the main() method:

Create an object obs of class Eigen

Call obs.accept()

Call obs.display()

Step 12: Stop







