## [**GitHub @Shavmik**](https://github.com/Shavmik)

## [**Insta @Shavmik**](https://www.instagram.com/shavmik/)

# **Pseudo Code** :

for Inputting a standard 3X3 matrix and returning its eigen values and eigen vectors-



START



CREATE a 3X3 matrix



READ the 9 elements of the matrix



CHECK if the matrix is Upper Triangular



IF matrix is Upper Triangular THEN

&#x20;   TAKE the diagonal elements as the three Eigen Values

&#x20;   DISPLAY the three Eigen Values

ELSE



&#x20;   FIND the Trace of the matrix



&#x20;   FIND M11, M22 and M33



&#x20;   FIND the coefficient of lambda



&#x20;   FIND the Determinant of the matrix



&#x20;   FORM the characteristic equation



&#x20;   FIND the Discriminant



&#x20;   IF Discriminant > 0 THEN

&#x20;       FIND the one real Eigen Value

&#x20;       DISPLAY the real Eigen Value

&#x20;       DISPLAY that the other two Eigen Values are complex

&#x20;   ELSE IF Discriminant = 0 THEN

&#x20;       FIND the three Eigen Values

&#x20;   ELSE

&#x20;       FIND the three Eigen Values

&#x20;   END IF



&#x20;   DISPLAY the three Eigen Values

END IF



FOR each Eigen Value



&#x20;   FIND (A - lambda I)



&#x20;   TAKE two rows of (A - lambda I)



&#x20;   FIND their cross product



&#x20;   IF cross product is zero THEN

&#x20;       TAKE another two rows

&#x20;       FIND their cross product

&#x20;   END IF



&#x20;   STORE the result as the Eigen Vector



END FOR



DISPLAY the three Eigen Vectors



END



