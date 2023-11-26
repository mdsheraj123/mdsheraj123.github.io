---
layout: post
title: >
    0 Dimensional Objects
hide_title: false
tags: []
excerpt_separator: <!--more-->
---
[
{% include image.html url="/assets/img/posts/dimensions.png" caption="](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg_R_gKoVBzR2yqPZgGaw-pVwuU_-6XThvE0Jw3eHmzWajMA_dXGdh_wn_CKGejDv8IeWW2KSh00XmlYyiwkVKKm5BRz_9K5pj9tN8e7Ad11ybMcDt5PbAR35HmfgApjUoyHTbYQrzqDKcBSVhjTht9xxqwlIG2kBFCcns2eETBT-WeSIlQBibMUonGWQ/s305/dimensions.png)" alt="" %}


I have experience with tensors from my M.Sc. in Physics \(used in Einstein's General Theory of Relativity math\) and recently from the TensorFlow ML library from Google \(used to define input space\).

A scalar is a zero rank tensor, and a vector is a first\-rank tensor. Tensors can be represented as N\-dimensional matrices \(scalar is a 0D matrix, a vector is a 1D matrix and so on\).

Vector is 1 Dimensional, a vector like position can be represented as x,y,z,.. spatial components. An array is enough to represent all components.

A rank 2 tensor like strain will be having xx, xy, xz,.. then yx, yy, yz.. and so on based on components.

A rank 3 tensor like torsion tensor will be having xxx, xxy, xxz,.. then xyx, xyy, xyz.. and so on based on components.

A rank 4 tensor like the Riemann tensor will be having xxxx, xxxy, xxxz,.. then xxyx, xxyy, xxyz.. and so on based on components.

But as per [https://math.stackexchange.com/questions/3613161/what\-is\-the\-number\-of\-dimensions\-of\-a\-scalar/3613606](https://math.stackexchange.com/questions/3613161/what-is-the-number-of-dimensions-of-a-scalar/3613606), Jordan says 
*
Dimension is a concept that doesn't apply that well to scalars. As Ninad Munshi said in their reply, dimension refers to the vector space in which the matrix/vector is embedded. Vector spaces have a "dimension"; vectors have "rank" \(which is basically just the number of elements in the vector; e.g. \[3,2\] has rank 2 while \[7,1,10\] has rank 3, etc\). Scalars don't really have either.

In other words, a scalar is not simply a rank 1 vector or a rank 1 matrix. Scalars are a different ingredient in the logic of linear algebra. They can be taken from a different space than the vector space \(called fields\). Often we take our scalars from the Real numbers, which is also where the elements of our vectors/matrices come from in many situations; but this is just coincidence. We could decide "in this scenario, we'll use only Integers to build our vectors, but use Real numbers as our scalars" \-\- and so on.

To summarize: scalars are different creatures from vectors; they come from a different realm. So, the concepts we use to describe vectors don't really apply to scalars.
*

Actually, I believe considering scalars as 0 dimensions is a convenient, consistent generalization like we usually do in Physics.

Consider geometry where a cube has 3 dimensions \(width, height and depth\), a square has 2 dimensions \(width and height\), a line has 1 dimension \(length\) and a point has 0 dimensions \(or you can say it has no dimensions\).

A point only has information in its embedding in other dimensional spaces like a point in 1D, 2D or 3D space.

A scalar can be represented as a size one \(one component\) array or a size one \(one component\) 2D matrix but it is not necessary to do so, it can live in 0 dimensions\!

Hence, scalars are 0 dimensional and point is also 0 dimensional.