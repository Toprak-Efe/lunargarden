# 1.0 Linear Equations in Linear Algebra
## 1.1 Systems of Linear Equations
#linearsystem #matrix
## 1.2 Row Reduction and Echelon Forms
#rowreduction #echelonform
## 1.3 Vector Equations
#vectors 
## 1.4 The Matrix Equation $Ax=b$
#matrices #matrixequation
## 1.5 Solution Sets of Linear Systems
#sets #solutionsets
## 1.7 Linear Independence
#linearindependence
## 1.8 Introduction to Linear Transformations
#lineartransformation
## 1.9 The Matrix of a Linear Transformation
# 2.0 Matrix Algebra
#matrixalgebra
## 2.1 Matrix Operations
#matrixoperations
## 2.2 The Inverse of a Matrix
## 2.3 Characterization of Invertible Matrices
# 3.0 Determinants
#determinants
## 3.1 Introduction to Determinants
## 3.2 Properties of Determinants
## 3.3 Cramer's Rule
#cramer #cramersrule
Cramer's Rule is an analytic technique derived from the geometry of determinants, that allows you to find a solution to a linear set of equations.

It is not faster than Gauss-Jordan Elimination for most cases, however, it is an useful method to have under your belt. 
### Derivation
This rule depends on the properties of determinants. Take, for example, the following equation describing the area between two vectors.
$$
\text{Area} =

||\hat{r_{1}} \times \hat{r_2}|| = 

||
\begin{bmatrix}
x \\ y
\end{bmatrix}
\times
\begin{bmatrix}
a \\ b
\end{bmatrix}
||
$$
If we were to then apply the transformation $A =\begin{bmatrix} k, l \\ m, n \end{bmatrix}$ to each of the vectors, we would observe the area get scaled by the determinant of the mentioned transformation.
$$
\text{Area}_{\text{new}} = \text{Area}\times\text{det(A)} =

||A\hat{r_{1}} \times A\hat{r_2}|| = 

||
A\begin{bmatrix}
x \\ y
\end{bmatrix}
\times
A\begin{bmatrix}
a \\ b
\end{bmatrix}
||
$$
For a linear transformation that symbolizes a linear system of equations, we can use this property to systematically seek out each coordinate.
$$
\begin{bmatrix}
a, \ c \\ b, \ d
\end{bmatrix}
\begin{bmatrix}
x_{1} \\ y_{1}
\end{bmatrix}
=
\begin{bmatrix}
x_{2} \\ y_{2}
\end{bmatrix}
$$
Consider the area between the first column vector $\begin{bmatrix} a \\ b \end{bmatrix}$ and the output vector $\begin{bmatrix} x_{2} \\ y_{2}\end{bmatrix}$. Instead of using cross products, we can just create a linear transformation and take it's determinant.
$$
\text{Area} = \text{det($\begin{bmatrix}a, \ x_{2} \\ b, \ y_{2}\end{bmatrix}$)}
$$
By the properties of determinants and matrix multiplication, we can equate this formula as follows:
$$
\text{det($\begin{bmatrix}a, \ x_{2} \\ b, \ y_{2}\end{bmatrix}$)} = \text{det($\begin{bmatrix}1, \ x_{1} \\ 0, \ y_{1}\end{bmatrix}\begin{bmatrix}a, \ c \\ b, \ d\end{bmatrix}$)} = \text{det($\begin{bmatrix}1, \ x_{1} \\ 0, \ y_{1}\end{bmatrix}$)}\times\text{det($\begin{bmatrix}a, \ c \\ b, \ d\end{bmatrix}$)}
$$
Now we can solve for $y_{1}$.
$$
\frac{\text{det($\begin{bmatrix}a, \ x_{2} \\ b, \ y_{2}\end{bmatrix}$)}}{\text{det($\begin{bmatrix}a, \ c \\ b, \ d\end{bmatrix}$)}} = y_{1}
$$
Similarly, we can also do the same operation for $x_{1}$.
$$
\frac{\text{det($\begin{bmatrix}x_{2}, \ c \\ y_{2}, \ d\end{bmatrix}$)}}{\text{det($\begin{bmatrix}a, \ c \\ b, \ d\end{bmatrix}$)}} = x_{1}
$$
### Conclusion
In conclusion, we can solve a specific component of the input vector in a linear transformation by calculating the **space** contained by the transformed vector and the rest of the column vectors, excepting the one that corresponds to the component we are searching for.
### Generalizing to Higher Dimensions
Then we take that area, and divide it by the determinant of the linear transformation, such that every column vector becomes orthogonal, and as a result the quantity at hand equates to the component of the input vector corresponding to the calculated direction.

For a general system of linear equations like below, we may discover the components as such,
$$
\begin{bmatrix}
a_{11}, \ a_{12}, \dots, a_{1n} \\ a_{21}, \ a_{22}, \dots, a_{2n} \\\vdots \\ a_{n1}, \ a_{n2}, \dots, a_{nn}
\end{bmatrix}
\begin{bmatrix}
b_{1} \\ b_{2} \\ \vdots \\ b_{n}
\end{bmatrix}
=
\begin{bmatrix}
c_{1} \\ c_{2} \\ \vdots \\ c_{n}
\end{bmatrix}
$$
To find $b_{k}$, we take the initial matrix and replace it's $k$-th column vector without output vector. Then divide the determinant of that expression with the determinant of the linear transformation itself.

For $k = 2$,
$$
b_{2} =
\frac{\text{det$(\begin{bmatrix}
a_{11}, b_{1}, \dots, a_{1n} \\
a_{21}, b_{2}, \dots, a_{2n} \\
\vdots \\
a_{n1}, b_{n}, \dots, a_{nn} \\
\end{bmatrix})$}}{\text{det$(\begin{bmatrix}
a_{11}, \ a_{12}, \dots, a_{1n} \\ a_{21}, \ a_{22}, \dots, a_{2n} \\\vdots \\ a_{n1}, \ a_{n2}, \dots, a_{nn}
\end{bmatrix})$
}}
$$

# 4.0 Vector Spaces
## 4.1 Vector Spaces and Subspaces
### Vector Spaces
#vectorspaces
A vector space is a non-empty set $V$ of objects, called vectors, which are defined on two operations called adition and multiplication by scalars (real numbers), subject to the ten axioms (or rules) listed below. The axioms must hold for all vectors $u, v$ and $w$ in $V$ and for all scalars $c$ and $d$.

> [!NOTE] Vector Space Properties
> 1. The sum of $u$ and $v$, denoted by $u+v$, is in $V$.
> 2. $u+v = v+u$.
> 3. $(u+v)+w = u+(v+w)$.
> 4. There is a zero vector $0$ in $V$ such that $u + 0 =  u$.
> 5. For each $u$ in $V$, there is a vector $-u$ in $V$ such that $u + (-u) = 0$.
> 6. The scalar multiple of $u$ by $c$, denoted by $cu$, is in $V$.
> 7. $c(u+v)=cu+cv$.
> 8. $(c+d)u=cu+du$.
> 9. $c(du)=(cd)u$.
> 10. $1u=u$.
>  
> Though technically $V$ is a real vector space, all of the theory also holds for a complex vector space as well.

> [!NOTE] Algebraic Properties of $\mathbb{R}^{n}$
> For all $u, v, w$ in $\mathbb{R}^{n}$ and all scalars $c$ and $d$:
> $$
> \begin{align}
> \text{(i)}& \ \ \ u+v = v+u \\
> \text{(ii)}& \ \ \ (u+v) + w = u + (v+w) \\
> \text{(iii)}& \ \ \ u + 0 = 0 + u = u \\
> \text{(iv)}& \ \ \ u + (-u) = -u + u = 0 \\
> \text{(iv)}& \ \ \ u + (-u) = -u + u = 0 \\
> \text{(v)}& \ \ \ c(u+v) = cu + cv \\
> \text{(vi)}& \ \ \ (c+d)u = cu + du \\
> \text{(vii)}& \ \ \ c(du) = (cd)u \\
> \text{(viii)}& \ \ \ 1u = u \\
> \end{align}
> $$
>

### Subspaces
#subspaces
## 4.2 Null Spaces, Column Spaces, Row Spaces, and Linear Transformations
### Null Space
#nullspace
The null space of an $m \times n$ matrix $A$, written as $\text{Nul}\ A$ is the set of all solutions of the homogeneous equation $Ax = 0$. In set notation,
$$
\text{Nul}\ A = \{ x : x \ \text{is in }\mathbb{R}^{n} \text{ and } Ax=0 \}
$$

> [!NOTE] Theorem
> The null space of an $m \times n$ matrix $A$ is a subspace of $\mathbb{R}^{n}$. Equivalently, the set of all solutions to a system $Ax = 0$ of $m$ homogeneous linear equations in $n$ unknowns is a subspace of $\mathbb{R}^{n}$.
### Column Space
#columnspace
The column space of an $m \times n$ matrix $A$, written as $\text{Col} \ A$ is the set of all linear combinations of the columns of $A$. If $A$ = $[a_{1}, a_{2}, \dots, a_{n}]$,
$$
\text{Col} \ A = \text{Span} \{ a_{1}, a_{2}, \dots, a_{n} \}
$$

> [!NOTE] Theorem
> The column space of a $m \times n$ matrix $A$ is a subspace of $\mathbb{R}^{m}$.
### Row Spaces
#rowspace
The row space of an $m \times n$ matrix $A$, written as $\text{Row} \ A$, is the set of all matrices that are a linear combination of the rows of $A$.

$$
\begin{align}
A &=
\begin{bmatrix}
a_{11}, \ a_{12},\ \dots, \  \ a_{1n} \\
a_{21}, \ a_{22},\ \dots, \  \ a_{2n} \\
\vdots \\
a_{n1}, \ a_{n2},\ \dots, \  \ a_{nn} 
\end{bmatrix}
= 
\begin{bmatrix}
r_{1} \\
r_{2} \\
\vdots \\
r_{n} \\
\end{bmatrix}
\\\\
\text{Row} \ A &= \text{Span} \{ r_{1}, r_{2}, \dots, r_{n}\}
\end{align}
$$
> [!NOTE] Theorem
> The transpose of a 
## 4.3 Linearly Independent Sets; Bases
#bases
An indexed set of vectors $\{v_{1}, \dots, v_{p}\}$ in $V$ is said to be linearly independent if the vector equation $c_{1}v_{1} + c_{2}v_{2} + \dots + c_{p}v_{p} = 0$ has only the trivial solution.

The set $\{v_{1}, \dots, v_{p}\}$ is said to be linearly dependent if the aforementioned vector equation has a nontrivial solution. That is, if there are some weights $c_{1}, \dots, c_{p}$, not all zero, such that the equation holds. In such a case, the equation is called a linear dependence relation among $\{v_{1}, \dots, v_{p}\}$.
## 4.4 Coordinate Systems

> [!NOTE] The Unique Representation Theorem
> Let $B = [b_{1}, b_{2}, \dots ,b_{n}]$ be a basis for the vector space $V$. Then for each $x$ in $V$, there exists an unique set of scalars $c_{1}, c_{2}, \dots , c_{3}$ such that,
> $$
> x = c_{1}b_{1} + c_{2}b_{2} + \dots + c_{n}b_{n}
> $$


## 4.5 Dimensions of a Vector Space

> [!NOTE] Assertion
> If a vector space $V$ has a basis $B = \{b_{1},\dots,b_{n} \}$ then any set in $V$ containing more than $n$ vectors must be linearly dependent.
> 

To prove the above, we may enlist an example of a set $B_{p} = \{u_{1},\dots,u_{p}\}$ with $p > n$. Because the existing basis $B = \{b_{1},\dots,b_{n} \}$ vectors and alongside them the vectors $u_{n+1},\dots, u_{p}$ are all in $B_{p}$, these vectors are linearly dependent with the set $B$ which is inside $B_{p}$. Hence, $B_{p}$ is linearly dependent.

> [!NOTE] The Basis Theorem
> Let $V$ be a $p-$dimensional vector space, $p \geq 1$. Any linearly independent set of exactly $p$ elements in $V$ is automatically a basis for $V$. Any set of exactly $p$ elements that spans $V$ is automatically a basis for $V$.
### The Dimensions of $\text{Nul} \ A$, $\text{Col} \ A$, and $\text{Row} \ A$
Since the dimensions of the null space and column space of an $m \times n$ matrix are referred to frequently, they have specific names:

The **rank** of an $m \times n$ matrix $A$ is the dimension of the column space, and the **nullity** of $A$ is the dimension of the null space.

The pivot columns of a matrix $A$ form a basis for $\text{Col} \ A$, so the rank of $A$ is just the number of pivot columns.
The row-reduced form presents non-zero rows that are equal to the pivot columns in number, which means $\text{Row} \ A = \text{Col} \ A$.

> [!Note] The Rank Theorem
> The dimensions of the column space and the null space of an $m \times n$ matrix $A$ satisfy the equation
> $$
> \text{rank} \ A + \text{nullity} \ A = \text{number of columns in }A
> $$

## 4.6 Change of Basis
In some applications, a problem is initially described with a specific basis $B$, however, for the sake of finding the solution we may often resort to changing that basis to simplify the algebra.

> [!QUESTION] Example
> Consider two bases $B = \{ b_{1}, b_{2} \}$ and $C = \{ c_{1}, c_{2} \}$ for a vector space $V$, such that
> $$
> b_{1} = 4c_{1}+c_{2} \ and \ b_{2} = -6c_{1} + c_{2}
> $$
> Suppose
> $$
> x = 3b_{1}+b_{2}
> $$
> That is, suppose $[x]_{B} = \begin{bmatrix}3 \\ 1\end{bmatrix}$. Find $[x]_{C}$.

In order to find the coordinates $x$ defined in terms of the base $C$, we need to decompose $x$ into $B$, and then decompose $B$ into the basis $C$. Since we know the former and latter in order, we may decompose $x$ in two steps.
$$
\begin{align}
b_{1} &=
\begin{bmatrix}
c_{1}, c_{2}
\end{bmatrix} 
\begin{bmatrix}
4 \\1
\end{bmatrix} \\
b_{2} &=
\begin{bmatrix}
c_{1}, c_{2}
\end{bmatrix} 
\begin{bmatrix}
-6 \\ 1
\end{bmatrix} \\
x &=
\begin{bmatrix}
b_{1}, b_{2}
\end{bmatrix} 
\begin{bmatrix}
3 \\1
\end{bmatrix} =
\begin{bmatrix}
4c_{1}+c_{2}, -6c_{1}+c_{2}
\end{bmatrix} 
\begin{bmatrix}
3 \\ 1
\end{bmatrix}
=
\begin{bmatrix}
c_{1}, c_{2}
\end{bmatrix}
\begin{bmatrix}
6 \\ 4
\end{bmatrix} 
\end{align}
$$
Interesting insight to be gained in this question, you can completely ignore $c_{1}$ and $c_{2}$ and the problem would simplify into a simple matrix multiplication.
$$
\begin{align}
b_{1} &=
\begin{bmatrix}
4 \\1
\end{bmatrix} \\
b_{2} &=
\begin{bmatrix}
-6 \\1
\end{bmatrix} \\
x &=
\begin{bmatrix}
b_{1}, b_{2}
\end{bmatrix} 
\begin{bmatrix}
3 \\1
\end{bmatrix}
=
\begin{bmatrix}
4, -6 \\ 1, \ \ 1
\end{bmatrix} 
\begin{bmatrix}
3 \\1
\end{bmatrix}
= 
\begin{bmatrix}
6 \\4
\end{bmatrix}
\end{align}
$$
The intuition is, matrix multiplications are essentially decompositions. Every operation is essentially counting how many of a certain basis vector we have, and how much of the corresponding column vector in the matrix we get as a result of that count.

A matrix is hence the perfect construct to contain the decomposition of vectors into certain bases. Essentially, we created a matrix $\begin{bmatrix}4, -6 \\ 1, \ \ 1 \end{bmatrix}$ that when multiplied with a vector whose basis is $B$, will be decomposed into the basis $C$ as a natural consequence of storing the $C$ decomposition of $B$'s basis vectors.

To get the inverse effect, that is to say, decompose $C$ into $B$, we may multiply an example vector $[x]_{C}$ by the inverse of that same matrix to get $[X]_{B}$.

In terms of $\hat{i}$ and $\hat{j}$, this makes sense. Because they are a basis in of themselves, hence, in future problems you might think of first decomposing a basis $B$ into this 'identity-basis' --Not a term I am making it up-- with a matrix multiplication, then composing it back into another basis $C$ with a reverse matrix multiplication. 
# 5.0 Eigenvalues and Eigenvectors
#eigenvalue #eigenvector #math #transform 

## 5.1 Eigenvectors and Eigenvalues
Although linear transformations impose a variety of movement upon vectors, for most transformations there are a specific set of vectors whose movement become a simple multiplication operation.
### Eigenvectors, Eigenvalues
> [!example] Definition
> An eigenvector of an $n \times n$ matrix $A$ is a nonzero vector $x$ such that $Ax = \lambda x$ for some scalar $\lambda$. A scalar $\lambda$ is called an eigenvalue of $A$ if there is a nontrivial solution x of $Ax = \lambda x$; such an x is called an eigenvector corresponding to $\lambda$.

We may solve for these eigenvalues by operating on the definitive equation of the eigenvalues.
$$
\begin{align}
Ax &= \lambda x \\
(A-\lambda I)x &= 0 \\
\end{align}
$$
$$
\begin{bmatrix}
a_{11} - \lambda & a_{22} & \dots & a_{1n} \\
a_{21} & a_{22} - \lambda & \dots & a_{2n} \\
\vdots & \vdots & \vdots & \vdots \\
a_{n1} & a_{n2} & \dots & a_{nn} - \lambda \\
\end{bmatrix}x = 0
$$
For $\lambda$ to be an eigenvalue there must be a non-zero set of $x$ such that the equation is satisfied.

> [!NOTE] Note
> An eigenvector must be non-zero by definition, however, the corresponding eigenvalue may equal zero. In that case, so must the determinant of the original matrix.
### Eigenspaces
#eigenspace
> [!EXAMPLE] Definition
> The set of all solutions $x$ for a specific eigenvalue $\lambda$, is called an eigenspace of $A$ corresponding to $\lambda$.
### Triangular Matrices
There are some special cases that make it very easy to calculate the eigenvalues of a matrix, such as when the matrix itself is a triangular type.

Such a matrix, will have eigenvalues that are direct correspondents of the values on its main diagonal.
## 5.2 The Characteristic Equation
#thecharacteristicequation
#thecharacteristicpolynomial 
In order to find the eigenvalues of a matrix $A$, we must solve for all scalars that satisfy the following equation,
$$
(A-\lambda I)x = 0
$$
such that there are nontrivial solutions. By the Invertible Matrix Theorem, this problem is equivalent to finding all $\lambda$ such that the matrix $A-\lambda I$ is not invertible. A matrix fails to be invertible precisely when its determinant is zero. So eigenvalues of $A$ are the solutions of the equation,
$$
\text{det}{[(A-\lambda I)]} = 0
$$
Which can be in actuality solved as a polynomial.
$$
(A-\lambda I) = \begin{bmatrix}
a_{11} - \lambda & a_{22} & \dots & a_{1n} \\
a_{21} & a_{22} - \lambda & \dots & a_{2n} \\
\vdots & \vdots & \vdots & \vdots \\
a_{n1} & a_{n2} & \dots & a_{nn} - \lambda \\
\end{bmatrix}
$$
$$
\text{det}[\begin{bmatrix}
a_{11} - \lambda & a_{22} & \dots & a_{1n} \\
a_{21} & a_{22} - \lambda & \dots & a_{2n} \\
\vdots & \vdots & \vdots & \vdots \\
a_{n1} & a_{n2} & \dots & a_{nn} - \lambda \\
\end{bmatrix}] = (a_{11}-\lambda)(a_{21}-\lambda)\dots(a_{nn}-\lambda) = 0
$$
The resulting polynomial equation, is called **the characteristic polynomial** of a matrix. Because the characteristic equation for an $n \times n$ matrix is an $n-$th degree polynomial, the equation has exactly $n$ roots. Including multiplicities, and complex roots.
### Similarity
#similarity
The next theorem illustrates one use of the characteristic polynomial, and it provides the foundation for several iterative methods used to approximate eigenvalues. Assuming that $A$ and $B$ are both $n \times n$ matrices, then $A$ is similar to $B$ if there is an invertible matrix $P$ such that $P^{-1}AP = B$, or, equivalently, $PBP^{-1} = A$.

> [!NOTE] Note
> If $n \times n$ matrices $A$ and $B$ are similar, then they have the same characteristic polynomial, and hence, the same eigenvalues (with same multiplicities).

## 5.3 Diagonalization
#diagonalization
A square matrix $A$ is said to be diagonalizable if $A$ is similar to a diagonal matrix, that is, if $A = PDP^-1$ for some invertible matrix $P$ and some diagonal matrix $D$.

> [!NOTE] The Diagonalization Theorem 
> An $n \times n$ matrix $A$ is diagonalizable if and only if $A$ has $n$ linearly independent eigenvectors.
> In fact, $A = PDP^-1$, with $D$ a diagonal matrix, if and only if the columns of $P$ are $n$ linearly eigenvectors of $A$. In this case, the diagonal entries of $D$ are eigenvalues of $A$ that correspond, respectively, to the eigenvectors in $P$.

Suppose that $A$ is an $n \times n$ matrix and that $\lambda_{1}$, and $\lambda_{2}$ are it's corresponding eigenvalues, with $x_{1}$, and $x_{2}$ being their respective eigenvectors. We can write the following equation and prove The Diagonalization Theorem off of it.
$$
A
\begin{bmatrix}
x_{1} & x_{2}
\end{bmatrix}
=
\begin{bmatrix}
\lambda_{1}x_{1} & \lambda_{2}x_{2}
\end{bmatrix}
=
\begin{bmatrix}
x_{1} & x_{2}
\end{bmatrix}
\begin{bmatrix}
\lambda_{1} & 0 \\ 0 & \lambda_{2}
\end{bmatrix}
$$
Right multiplying each side by $(\begin{bmatrix}x_{1} & x_{2}\end{bmatrix})^-1$ yields us a solution for $A$.
$$
A =
\begin{bmatrix}
x_{2} & x_{2}
\end{bmatrix}
\begin{bmatrix}
\lambda_{1} & 0 \\ 0 & \lambda_{2}
\end{bmatrix}
(\begin{bmatrix}
x_{2} & x_{2}
\end{bmatrix})^-1
$$
The matrix $\begin{bmatrix}x_{1} & x_{2}\end{bmatrix}$ is called the eigenvector matrix, while the matrix $\begin{bmatrix}\lambda_{1} & 0 \\ 0 & \lambda_{2}\end{bmatrix}$ is called the eigenvalue matrix. As a result of this computation we have now diagonalized our matrix $A$.

We may diagonalize any matrix by solving for it's eigenvalues through the characteristic polynomial, then finding the corresponding eigenvectors and putting them together.
## 5.4 Eigenvectors of Linear Transformations
#eigenvalue #eigenvector
Let $V$ be a vector space. An **eigenvector** of a linear transformation $T : V \to V$ is a nonzero vector $x$ in $V$ such that $T(x) = \lambda x$ for some scalar $\lambda$. A scalar $\lambda$ is called an **eigenvalue** of $T$ if there is a nontrivial solution $x$ of $T(x) = \lambda x;$ such an $x$ is called an **eigenvector** corresponding to $\lambda$.

## 5.5 Complex Eigen Values
#eigenvalue  #eigenvector  #complex
The characteristic equation of an $n \times n$ matrix involves a polynomial of degree $n$, the equations always has exactly $n$ roots, counting multiplicities, provided that $\text{possibly complex roots are included}$.
$$
\begin{bmatrix}
a, &-b \\
b, &a
\end{bmatrix}
$$
For the matrix above, the characteristic polynomial is as follows.
$$
(a-\lambda)^{2} + b^2 = 0
$$
The solution to this polynomial can be deduced by using the quadratic equation.
$$
\lambda = a \pm \sqrt{a^{2} - (a^2 + b^2)} = a \pm ib
$$
Withstanding the calculated eigenvalue, we can find the corresponding eigenvectors by setting up the identity equation. Let's begin with $a-ib$.
$$
\begin{bmatrix}
a- (a-ib), &-b \\
b, &a - (a-ib)
\end{bmatrix}
=
\begin{bmatrix}
ib, &-b \\
b, &ib
\end{bmatrix}
$$


$$
\begin{bmatrix}
ib, &-b \\
b, &ib
\end{bmatrix}
\begin{bmatrix}
x \\ y
\end{bmatrix}
=
\begin{bmatrix}
i, &-1 \\
1, &i
\end{bmatrix}
\begin{bmatrix}
x \\ y
\end{bmatrix}
=
\begin{bmatrix}
0 \\ 0
\end{bmatrix}
$$
$$
ix-y=0, \ \ \
x+iy=0
$$
$$
x = -iy
$$
$$
\text{The eigenvector for eigenvalue} \ \lambda=a-ib \  \text{is}
\begin{bmatrix}
1\\
-i
\end{bmatrix}
$$
Following this, for the eigenvalue  $a+ib$ we get the eigenvector $\begin{bmatrix}1 \\ i \end{bmatrix}$.
# 6.0 Orthogonality and Least Squares
#orthogonality #leastsquares
## 6.1 Inner Product, Length and Orthogonality
#innerproduct #dotproduct #vectorlength #orthogonality 
### The Inner Product
If $u$ and $v$ are vectors in $\mathbb{R}^{n}$, their inner product (dot product) is defined the sum of the matching multiplicative of their elements.
$$
u \cdot v= \begin{bmatrix} u_{1} \\ u_{2} \\ \vdots \\u_{n} \end{bmatrix}\cdot\begin{bmatrix} v_{1} \\ v_{2} \\ \vdots \\v_{n} \end{bmatrix} = \begin{bmatrix} u_{1}, u_{2}, \dots ,u_{n} \end{bmatrix}\begin{bmatrix} v_{1} \\ v_{2} \\ \vdots \\v_{n} \end{bmatrix} = u_{1}v_{1}+u_{2}v_{2} + \dots + u_{n}v_{n}
$$
### The Length of a Vector
For $v$ in $\mathbb{R}^{n}$, it's length is defined as the square root of it's inner product with itself. In other words, the euclidean length of the vector from the origin to where it stands in $\mathbb{R}^{n}$.

$$
||v|| = \sqrt{v\cdot v} = \sqrt{v_{1}^{2} + v_{2}^{2} + \dots + v_{n}^{2}}, \ \ \ \text{and} \ \ \ ||v||^{2} = v\cdot v
$$
For any scalar $c$, the length of $cv$ is $|c|$ times the length of $v$. That is,
$$
||cv|| = |c|||v||
$$
### Distance in $\mathbb{R}^{n}$
#distance #euclideandistance
For $u$ and $v$ in $\mathbb{R}^{n}$, the distance between $u$ and $v$, written as dist $(u, v)$, is the length of the vector $u-v$. That is,
$$
\text{dist}(u, v)= ||u-v||
$$
### Orthogonal Vectors
#orthogonality
The rest of the theorems and theory is built upon the assumption that the properties of perpendicularity holds up in dimensions above $n=3$.
Consider $\mathbb{R}^{2}$ or $\mathbb{R}^3$ and two vectors $u$ and $v$, these two vectors are orthogonal only if the distance between their endpoints stay constant when one of the vectors are flipped around.

![[Pasted image 20231219145214.png]]

Using The Pythagorean Theorem, two vectors $u$ and $v$ are orthogonal if and only if $||u+v||^2 = ||u||^2 + ||v||^2$.
### Orthogonal Complements
#orthogonality #orthogonalcomplements
For a subspace $W$ of $\mathbb{R}^n$ and vector $z$, the vector $z$ is said to be an **orthogonal** to $W$ if for every vector $u$ in $W$, orthogonality is true between $u$ and $z$.

The set of all vector $z$ perpendicular to the subspace $W$ is called an **orthogonal compliment**, and is denoted by $W^{\perp}$ (and read as "$W$ perp").
$$
L = W^{\perp} \ \ \ \text{and} \ \ \ W = L^{\perp}
$$
![[Pasted image 20231219145921.png]]

## 6.2 Orthogonal Sets
#sets
A set of vectors $\{ {u_{1},\dots,u_{p}} \}$ in $\mathbb{R}^n$ is said to be an **orthogonal set** if each pair of distinct vectors from the set is orthogonal, that is, if $u_{i}\cdot u_{j}=0$ whenever $i \neq j$.
## 6.3 Orthogonal Projections
#projection #orthogonalprojection
Given a nonzero vector $u$ in $\mathbb{R}^n$, consider the problem of decomposing a vector $y$ in $\mathbb{R}^n$ into sum of two vectors, one a multiple of $u$ and the other orthogonal to $u$. We wish to write,
$$
y = \hat{y}+z
$$
where $\hat{y} = \alpha u$ for some scalar $\alpha$ and $z$ is some vector orthogonal to $u$.
![[Pasted image 20231220131656.png]]
The constant $\alpha$ can be found by taking the dot product of the vector $u$ with the vector $y$, then dividing the resulting product sum with the length of the vector $u$, twice so in fact. First will give us the length of $\hat{y}$, the second will give us $\alpha$ through the formula $\hat{y} = \alpha u$.
### Orthonormal Sets
#orthonormal #sets 
Orthonormal sets are orthogonal sets, whose vectors have the length of $1$, are thus normalized and meet the requirements for following equation to hold true,
$$
\begin{align}
&S = \{u_{1}, u_{2},\dots,u_{n} \} \\ \\
&||u_{1}|| = 1 \\
&||u_{2}|| = 1 \\
&\vdots \\
&||u_{n}|| = 1 \\
\end{align}
$$

> [!Note] The Best Approximation Theorem
> Let $W$ be a subspace of $\mathbb{R}^{n}$, let $y$ be any vector in $\mathbb{R}^{n}$, and let $\hat{y}$ be the orthogonal projection of $y$ onto $W$. Then $\hat{y}$ is the closest point in $W$ to $y$, in the sense that
> $$
> ||y-\hat{y}|| < ||y-v||
> $$
> for all $v$ in $W$ distinct from $\hat{y}$.
## 6.4 The Gram-Schmidt Process
#sets   #gram-schmidt #orthogonalization
For a non-orthogonal set $S = \{u_{1}, u_{2},\dots,u_{n} \}$, there is a simple algorithm that allows us to transform it into an orthogonal set $S_{o}=\{e_{1}, e_{2},\dots,e_{n} \}$, called **The Gram-Schmidt Process**.
The formula is as follows:

$$
\begin{align}
v_{1} &= u_{1} \\
v_{2} &= u_{2} - \text{proj}_{v_{1}}(u_{2}) \\
v_{3} &= u_{3} - \text{proj}_{v_{1}}(u_{2}) - \text{proj}_{v_{2}}(u_{2})\\
\vdots \\
v_{n} &= v_{n} \sum_{j = 1}^{n-1} \text{proj}_{v_{j}}(u_{n}) \\ \\
&\text{Normalizing the set,} \\ \\
e_{1} &= \frac{v_{1}}{||v_{1}||} \\
e_{2} &= \frac{v_{2}}{||v_{2}||} \\
e_{3} &= \frac{v_{3}}{||v_{3}||} \\
\vdots \\
e_{n} &= \frac{v_{n}}{||v_{n}||} \\
\end{align}
$$
Now, we have an orthonormal set of vectors $S$.
### QR Factorization of Matrices
If an $m \times n$ matrix $A$ has linearly independent columns $x_{1},\dots,x_{n}$, then applying the Gram-Schmidt process (with normalizations) to $x_{1},\dots,x_{n}$ amounts to factoring $A$, as described in the next theorem.

> [!NOTE] The QR Factorization
> If $A$ is an $m \times n$ matrix with linearly independent columns, then $A$ can be factored as $A = QR$, where $Q$ is an $m \times n$ matrix whose columns form an orthonormal basis for $\text{Col} \ A$ and $R$ is an $n \times n$ upper triangular invertible matrix with positive entries on its diagonal.

This is driven from the intermediate process of the Gram-Schmidt process, where we can find the vectors $v_{1}, v_{2}, \dots, v_{n}$ as a composition of the projected vectors with the original $u$ vectors.
## 6.5 Least Squares Problems
In most cases of a matrix equation, the system will be inconsistent, and a solution will not exist. For $Ax = b$, the best we can do is to find an $x$ that will make $Ax$ be as close to $b$ as possible.

The general least-squares problem is to find an $x$ that makes $||Ax - b||$ as small as possible.

> [!NOTE]
> If $A$ is $m \times n$ and $b$ is in $\mathbb{R}^{m}$, a least-squares solution of $Ax = b$ is an $\hat{x}$ in $\mathbb{R}^{n}$ such that
> $$
> ||b - A\hat{x}|| \leq ||b - Ax||
> $$
> for all $x$ in $\mathbb{R}^{n}.$

### Solution of the General Least-Squares Problem
#### Projection
##### Using Gram Schmidt
Let's think about this geometrically, the above note states the least-square solution to essentially be the vector $A\hat{x}$ within the column space of $A$ that is *closest* to the vector $b$.

In the quintessential, we just need to project $b$ into the column space $A$. For most cases however, $A$ will not be an orthogonal matrix, for which we can use the Gram-Schmidt Process to orthogonalize it and then project the vector $b$ into the resulting orthogonalized matrix.

Then problem is resolved once we have the projection of $b$, as it is equal to the $\hat{x}$ we are looking for.
##### Using QR Factorization
Very similar to using Gram Schmidt, though far more elegant. 
Let $\hat{x} = R^-1Q^Tb$. Then,
$$A\hat{x} = QR\hat{x} = QRR^{-1}Q^Tb=QQ^Tb$$
By the theorem we know that $Q$ in $A = QR$ forms an orthonormal basis for $\text{Col} \ A$. Hence, $QQ^Tb$ is the orthogonal projection $\hat{b}$ of $b$ onto $\text{Col} \ A$. A lot to unpack here, indeed.

Geometrically, the operation $QQ^Tb$ accomplishes two things. First, by transforming $b$ with $Q^T$ we decompose it into the $Q$ basis. Then by transforming it with $Q$, we compose it back into $R^{n}$. The parts of $b$ that is orthogonal to the space created by $Q$ are simply chipped away by the two consecutive transformatioons, and all we are left with is it's projection.
#### Normal Equations
#hessian
$$
A^{T}Ax=A^{T}b
$$
Why the normal equations? To find out you need to be slightly insane, and really cool with calculus.
In general, we want to minimize
$$
f(x) = ||b - Ax||^2 = (b-Ax)^T(b-Ax) = b^Tb -x^TA^Tb-b^TAx+x^TA^TAx
$$
If $x$ is a global minimum of $f$, then its gradient $\nabla f(x)$ is the zero vector. Let's take the gradient of $f$ remembering that,
$$
\nabla f(x) = \begin{pmatrix}\frac{\partial f}{\partial x_{1}} \\ \vdots \\ \frac{\partial f}{\partial x_{2}}\end{pmatrix}
$$
This means we have to differentiate the four terms $b^Tb$, $-x^TA^Tb$, $-b^TAx$ and $x^TA^TAx$. Do not fret, hold onto these terms, it will get simpler.

If you do the arithmetic by hand we can discover a peculiar feature of the derivative in linear algebra.
$$
\begin{align}
f(x) &= x^T v =
\begin{bmatrix}
x_{1} & x_{2} & \dots &x_{n}
\end{bmatrix}
\begin{bmatrix}
v_{1} \\ v_{2} \\ \vdots \\ v_{n}
\end{bmatrix}
=
x_{1}v_{1}+x_{2}v_{2}+\dots+x_{n}v_{n} \\
\nabla{f} &=
\begin{bmatrix}
\frac{\partial f}{\partial x_{1}} \\
\frac{\partial f}{\partial x_{2}} \\
\vdots \\
\frac{\partial f}{\partial x_{n}} \\
\end{bmatrix}
=
\begin{bmatrix}
v_{1} \\
v_{2} \\
\vdots \\
v_{n}
\end{bmatrix}
=v
\end{align}
$$
In conclusion, the gradient of $x^Tv$ in terms of $x$ is $v$ itself. If we go the other way around, and seek the derivative of $vx$ instead, with the vector $x$ being at the right side,
$$
\begin{align}
f(x) &= vx =
\begin{bmatrix}
v_{1} & v_{2} & \dots & v_{n}
\end{bmatrix}
\begin{bmatrix}
x_{1} \\
x_{2} \\
\vdots \\
x_{n}
\end{bmatrix}
= x_{1}v_{1}+x_{2}v_{2}+\dots+x_{n}v_{n} \\
\nabla{f} &=
\begin{bmatrix}
\frac{\partial f}{\partial x_{1}} \\
\frac{\partial f}{\partial x_{2}} \\
\vdots \\
\frac{\partial f}{\partial x_{n}} \\
\end{bmatrix}
=
\begin{bmatrix}
v_{1} \\
v_{2} \\
\vdots \\
v_{n}
\end{bmatrix}
=v^T
\end{align}
$$
We may now observe that taking the derivative of $vx$, will simply return the transpose of the left side. For cases with combinations of $x$ and $x^T$, chain rule may be aptly applied. Going back to our conundrum, we can easily find the gradintes with the above proof.
$$
\begin{align}
f(x) &= b^Tb -x^TA^Tb-b^TAx+x^TA^TAx \\
\nabla{f} &= 0 -A^Tb-A^Tb +A^TAx+A^TAx \\
\nabla{f} &= 2A^TAx-2A^Tb
\end{align}
$$
Equating the gradient to zero, we get the following formula.
$$
A^Tb = A^TAx
$$
Without going into much detail, the solutions to this equation will return us the minima and the maximum, how do we know that it is the global minimum and not a saddle point, or a global minimum? We take a look at it's "second derivative", or in other words, the Hessian.
$$
Hf=2A^TA
$$
## 6.7 Inner Product Space
The inner product space is not yet another inherent property of vectors, it is the generalization of the operation that is the dot product, to other; more varied vector spaces that have different rules compared to our well acquainted $\mathbb{R^n}$ space.

> [!Example] Definition
> An inner product on a vector space $V$ is a function that, to each pair of vectors $u$ and $v$ in $V$, associates a real number $\langle u, v\rangle$ and satisfies the following axioms, for all $u$, $v$ and $w$ in $V$ and all scalars $c$:
> 1. $\langle u, v \rangle = \langle v, u\rangle$
> 2. $\langle u+v, w\rangle = \langle u, w\rangle + \langle v, w\rangle$
> 3. $\langle cu, v\rangle = c\langle u, v\rangle$
> 4. $\langle u, u\rangle \leq 0$ and $\langle u, u\rangle = 0$ if and only if $u = 0$.
> 
> A vector space with an inner product is called an inner product space.

The definition is akin to saying that a vector space with a defined addition operation is called an addition space (not true... it might be idek), which might be confusing.

No matter, nearly everything discussed in this chapter for $\mathbb{R}^n$ is true for all inner product spaces.
### Lengths, Distances, and Orthogonality
Let's redefine the terms length, distance and orthogonality to include inner product spaces.

Let $V$ be an inner product space, with the inner product denoted by $\langle u, v \rangle$. Just as in $\mathbb{R}^{n}$, we define the length, or norm, of a vector $v$ to be scalar,
$$
||v|| = \sqrt{\langle v, v\rangle}
$$
Equivalently, $||v||^2 = \langle v, v \rangle$. (This definition makes sense because $\langle v, v \rangle \leq 0$, but the definition *does not* say that $\langle v, v \rangle$ is a "sum of squares," because $v$ need not be an element of $\mathbb{R}^{n}$.)

A unit vector is one whose length is 1. The distance between $u$ and $v$ is $||u-v||$. Vectors $u$ and $v$ are orthogonal if $\langle u,v \rangle = 0$.
### Two Inequalities
Given a vector $v$ in an inner product space $V$ and given a finite-dimensional subspace $W$, we may apply the Pythagorean Theorem to the orthogonal decomposition of $v$ with respect to $W$ and obtain
$$
||v||^2 = ||\text{proj}_{W}v||^2 + ||v -\text{proj}_{W}v||^2
$$
In particular, this shows that the norm of the projection of $v$ goes onto W does not exceed the norm of $v$ itself. This simple observation leads to the following important equality.

> [!Example] The Cauchy-Schwarz Inequality
> For all $u$, $v$ in $V$,
> $$
> |\langle u,v \rangle| \leq ||u|| \ ||v||
> $$

> [!Example] The Triangle Inequality
> For all $u$, $v$ in $V$,
> $$
> ||u + v|| \leq ||u|| + ||v||
> $$

