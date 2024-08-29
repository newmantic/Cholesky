# Cholesky


Cholesky Decomposition is a matrix factorization technique used specifically for symmetric, positive-definite matrices. It decomposes a matrix A into the product of a lower triangular matrix L and its transpose L^T. This decomposition is particularly useful in numerical methods for solving linear systems, matrix inversion, and other applications in linear algebra.


Matrix A:
Let A be an n x n symmetric, positive-definite matrix. Cholesky decomposition expresses A as:
A = L * L^T
Where:
L is an n x n lower triangular matrix.
L^T is the transpose of L, which is an upper triangular matrix.

Lower Triangular Matrix L:
A lower triangular matrix L is a matrix where all the elements above the main diagonal are zero:
L = [ l11  0   0  ...  0  ]
    [ l21 l22  0  ...  0  ]
    [ l31 l32 l33 ...  0  ]
    [  .   .   .  ...  .  ]
    [ ln1 ln2 ln3 ... lnn ]
    
Positive-Definite Matrix:
A matrix A is positive-definite if, for any non-zero vector x, the quadratic form x^T * A * x is positive:
x^T * A * x > 0  for all x ≠ 0
Positive-definite matrices have all positive eigenvalues, and their leading principal minors are all positive.


The Cholesky decomposition is performed by iterating through each element of the matrix L and calculating its value based on the values of previously calculated elements.

Initialize: Start with an empty matrix L with zeros.

Diagonal Elements:
Calculate the diagonal elements L[i][i] as the square root of the difference between the corresponding diagonal element of A and the sum of the squares of the elements in the current row up to i-1:
L[i][i] = sqrt(A[i][i] - sum(L[i][k]^2 for k = 1 to i-1))

Off-Diagonal Elements:
For the elements below the diagonal (L[i][j] where i > j), calculate them as the difference between the corresponding element of A and the sum of the products of the elements in the current row and column up to j-1, divided by the diagonal element L[j][j]:
L[i][j] = (A[i][j] - sum(L[i][k] * L[j][k] for k = 1 to j-1)) / L[j][j]
Set all elements above the diagonal in L to zero, and set L[i][i] for all i.



Given a matrix A:
A = [ 4  12 -16 ]
    [ 12  37 -43 ]
    [-16 -43  98 ]
We want to decompose A into L and L^T such that A = L * L^T.

Compute L:
Use the Cholesky decomposition algorithm to compute the elements of L:
L[1, 1] = sqrt(4) = 2
L[2, 1] = 12 / 2 = 6
L[2, 2] = sqrt(37 - 6^2) = 1
L[3, 1] = -16 / 2 = -8
L[3, 2] = (-43 - (6 * -8)) / 1 = 5
L[3, 3] = sqrt(98 - (-8^2 + 5^2)) = 3

Transpose L to Get L^T:
The transpose L^T is the upper triangular matrix corresponding to L.
