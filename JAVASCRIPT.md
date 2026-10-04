# **JAVASCRIPT:**

//Java program to input an standard 3X3 matrix and return its eigen values and eigen vectors\*/

import java.util.\*;

/\*I haven't used any complex third party mathematical libraries like 

&#x20; Apache Commons Math or EJML \*/ 

class Eigen //normal class decleration

{

&#x20;   Scanner sc = new Scanner(System.in); //will be using Scanner to input values by user

&#x20;   double\[]\[] matrix = new double\[3]\[3];



&#x20;   Eigen()

&#x20;   {

&#x20;       int n = matrix.length;

&#x20;   }



&#x20;   void accept()

&#x20;   {

&#x20;       System.out.println("Please enter the elements of the 3X3 matrix row by row");



&#x20;       for(int i = 0; i < 3; i++)

&#x20;       {

&#x20;           for(int j = 0; j < 3; j++)

&#x20;           {

&#x20;               matrix\[i]\[j] = sc.nextDouble();

&#x20;           }

&#x20;       }



&#x20;       System.out.println("\*All the inputs by the user are complete");

&#x20;   }



&#x20;   boolean checkUT()

&#x20;   { // this function basically tries to avoid the exception case to execute faster

&#x20;       for(int i = 0; i < 3; i++)

&#x20;       {

&#x20;           for(int j = 0; j < i; j++)

&#x20;           {

&#x20;               if(matrix\[i]\[j] != 0.0)

&#x20;               {

&#x20;                   System.out.println("Matrix doesnt fall under UT exception moving onto the real calculations");

&#x20;                   return false;

&#x20;               }

&#x20;           }

&#x20;       }

&#x20;       // assigning the Eigen Values (EV) to the diagonal elements of the UT matrix

&#x20;       double EV1 = matrix\[0]\[0];

&#x20;       double EV2 = matrix\[1]\[1];

&#x20;       double EV3 = matrix\[2]\[2];



&#x20;       System.out.println("Matrix falls under UT exception");

&#x20;       System.out.println("Eigen Value 1 = " + EV1 + "\\n" +

&#x20;                          "Eigen Value 2 = " + EV2 + "\\n" +

&#x20;                          "Eigen Value 3 = " + EV3);



&#x20;       return true;

&#x20;   }



&#x20;   double\[] EigenValues(double\[]\[] matrix)

&#x20;   {

&#x20;       if(checkUT() == true)

&#x20;       {

&#x20;           return new double\[]

&#x20;           {

&#x20;               matrix\[0]\[0],

&#x20;               matrix\[1]\[1],

&#x20;               matrix\[2]\[2]

&#x20;           };

&#x20;       }

/\*main formula used- λ^3 - Tr(A)λ^2 + (M11 + M22 + M33)λ - det(A) = 0

formula for Eigen Values used here det(A- lambda\*I)=0

also Trace = lambda1+lamda2+lamda3 do note it\*/

&#x20;       double Tr = matrix\[0]\[0] + matrix\[1]\[1] + matrix\[2]\[2]; 

&#x20;       //sum of the main diagonal 

&#x20;       double M11 = matrix\[1]\[1] \* matrix\[2]\[2] -

&#x20;                    matrix\[1]\[2] \* matrix\[2]\[1];



&#x20;       double M22 = matrix\[0]\[0] \* matrix\[2]\[2] -

&#x20;                    matrix\[0]\[2] \* matrix\[2]\[0];



&#x20;       double M33 = matrix\[0]\[0] \* matrix\[1]\[1] -

&#x20;                    matrix\[0]\[1] \* matrix\[1]\[0];

//here we were basically finding the minor of the matrix

&#x20;       double coeff = M11 + M22 + M33;



&#x20;       double det =

&#x20;           matrix\[0]\[0] \* M11

&#x20;           - matrix\[0]\[1] \* (matrix\[1]\[0] \* matrix\[2]\[2] -

&#x20;                            matrix\[1]\[2] \* matrix\[2]\[0])

&#x20;           + matrix\[0]\[2] \* (matrix\[1]\[0] \* matrix\[2]\[1] -

&#x20;                            matrix\[1]\[1] \* matrix\[2]\[0]);



&#x20;       double a = -Tr;

&#x20;       double b = coeff;

&#x20;       double c = -det;



&#x20;       double p = b - (a \* a) / 3.0;

&#x20;       double q = (2.0 \* a \* a \* a) / 27.0 - (a \* b) / 3.0 + c;



&#x20;       double Discrim = (q \* q) / 4.0 + (p \* p \* p) / 27.0;



&#x20;       double\[] EV = new double\[3];



&#x20;       if(Discrim > 0)

&#x20;       {

&#x20;           double u = Math.cbrt(-q / 2.0 + Math.sqrt(Discrim));

&#x20;           double v = Math.cbrt(-q / 2.0 - Math.sqrt(Discrim));



&#x20;           EV\[0] = u + v - a / 3.0;



&#x20;           System.out.println("Only one real eigen value exist:");

&#x20;           System.out.println("Eigen Value 1 = " + EV\[0]);

&#x20;           System.out.println("The other two eigen values are complex.");



&#x20;           return EV;

&#x20;       }

&#x20;       else if(Math.abs(Discrim) < 1e-10)

&#x20;       {

&#x20;           double u = Math.cbrt(-q / 2.0);



&#x20;           EV\[0] = 2.0 \* u - a / 3.0;

&#x20;           EV\[1] = -u - a / 3.0;

&#x20;           EV\[2] = -u - a / 3.0;

&#x20;       }

&#x20;       else

&#x20;       {

&#x20;           double r = 2.0 \* Math.sqrt(-p / 3.0);



&#x20;           double theta = Math.acos((3.0 \* q / (2.0 \* p)) \* Math.sqrt(-3.0 / p));



&#x20;           EV\[0] = r \* Math.cos(theta / 3.0) - a / 3.0;

&#x20;           EV\[1] = r \* Math.cos((theta + 2.0 \* Math.PI) / 3.0) - a / 3.0;

&#x20;           EV\[2] = r \* Math.cos((theta + 4.0 \* Math.PI) / 3.0) - a / 3.0;

&#x20;       }



&#x20;       System.out.println("Eigen Value 1 = " + EV\[0] + "\\n" +

&#x20;                          "Eigen Value 2 = " + EV\[1] + "\\n" +

&#x20;                          "Eigen Value 3 = " + EV\[2]);



&#x20;       return EV;

&#x20;   }



&#x20;   double\[]\[] EigenVectors(double\[]\[] matrix, double\[] EV)

&#x20;   {

&#x20;       double\[]\[] vectors = new double\[3]\[3];

//calculates one eigen vector for each of the three eigen values

&#x20;       for(int n = 0; n < 3; n++)

&#x20;       {

&#x20;           double lambda = EV\[n];



&#x20;           double\[]\[] B = new double\[3]\[3];



&#x20;           for(int i = 0; i < 3; i++)

&#x20;           {

&#x20;               for(int j = 0; j < 3; j++)

&#x20;               {

&#x20;                   if(i == j)

&#x20;                   {

&#x20;                       B\[i]\[j] = matrix\[i]\[j] - lambda;

&#x20;                   }

&#x20;                   else

&#x20;                   {

&#x20;                       B\[i]\[j] = matrix\[i]\[j];

&#x20;                   }

&#x20;               }

&#x20;           }

//the three elements in the X matrix are been assigned here

&#x20;           double x1 = B\[0]\[1] \* B\[1]\[2] -  B\[0]\[2] \* B\[1]\[1];

&#x20;           double x2 = B\[0]\[2] \* B\[1]\[0] - B\[0]\[0] \* B\[1]\[2];

&#x20;           double x3 = B\[0]\[0]  \* B\[1]\[1] - B\[0]\[1] \* B\[1]\[0];



&#x20;           if(Math.abs(x1) < 1e-10 \&\&

&#x20;              Math.abs(x2) < 1e-10 \&\&

&#x20;              Math.abs(x3) < 1e-10)

&#x20;           {

&#x20;               x1 = B\[1]\[1] \* B\[2]\[2] - B\[1]\[2] \* B\[2]\[1];

&#x20;               x2 = B\[1]\[2] \* B\[2]\[0] - B\[1]\[0] \* B\[2]\[2];

&#x20;               x3 = B\[1]\[0] \* B\[2]\[1] - B\[1]\[1] \* B\[2]\[0];

&#x20;           }



&#x20;           vectors\[n]\[0] = x1;

&#x20;           vectors\[n]\[1] = x2;

&#x20;           vectors\[n]\[2] = x3;

&#x20;       }



&#x20;       System.out.println("Eigen Vectors:");



&#x20;       for(int i = 0; i < 3; i++)

&#x20;       {

&#x20;           System.out.println("For Eigen Value " + EV\[i] + " = \[" +

&#x20;                              vectors\[i]\[0] + ", " +

&#x20;                              vectors\[i]\[1] + ", " +

&#x20;                              vectors\[i]\[2] + "]");

&#x20;       }



&#x20;       return vectors;

&#x20;   }



&#x20;   void display()

&#x20;   {

&#x20;       double\[] EV = EigenValues(matrix);

&#x20;       EigenVectors(matrix, EV);

&#x20;   }



&#x20;   public static void main()

&#x20;   {

&#x20;       Eigen obs = new Eigen();



&#x20;       obs.accept();

&#x20;       obs.display();

&#x20;   }

}



