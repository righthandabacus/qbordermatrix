# qbordermatrix

Draw a matrix in LaTeX with any border columns

Example:

```latex
\documentclass{article}
\usepackage{qbordermatrix}
\begin{document}
\hrule y\vrule$\bordermatrix[\{\}]{%
0 &   1 &2^{2^2}& 3 & \displaystyle\frac{4}{2} \cr
a & x_1 & y_2 & z_1 & t_1 \cr
b & x_3 & y_4 & z_2 & t_2 \cr
c & x_5 & y_6 & z_3 & t_3 \cr
d &   1 &2^{2^2}& 3 & \displaystyle\frac{4}{2} \cr
}$\vrule bordermatrix\hrule

\hrule y\vrule$\bordermatrix*[\{\}]{%
0 &   1 &2^{2^2}& 3 & \displaystyle\frac{4}{2} \cr
a & x_1 & y_2 & z_1 & t_1 \cr
b & x_3 & y_4 & z_2 & t_2 \cr
c & x_5 & y_6 & z_3 & t_3 \cr
d &   1 &2^{2^2}& 3 & \displaystyle\frac{4}{2} \cr
}$\vrule bordermatrix*\hrule

\hrule y\vrule$\qbordermatrix[\{\}]{nesw}{%
0 &   1 &2^{2^2}& 3 & \displaystyle\frac{4}{2} \cr
a & x_1 & y_2 & z_1 & t_1 \cr
b & x_3 & y_4 & z_2 & t_2 \cr
c & x_5 & y_6 & z_3 & t_3 \cr
d &   1 &2^{2^2}& 3 & \displaystyle\frac{4}{2} \cr
}$\vrule qbordermatrix-nesw\hrule

\hrule y\vrule$\qbordermatrix[\{\}]{ns}{%
0 &   1 &2^{2^2}& 3 & \displaystyle\frac{4}{2} \cr
a & x_1 & y_2 & z_1 & t_1 \cr
b & x_3 & y_4 & z_2 & t_2 \cr
c & x_5 & y_6 & z_3 & t_3 \cr
d &   1 &2^{2^2}& 3 & \displaystyle\frac{4}{2} \cr
}$\vrule qbordermatrix-ns\hrule

\end{document}
```

This package aims to be a more flexible `\bordermatrix` for LaTeX. It provides three commands:

- `\bordermatrix` - similar to the Knuth's version
- `\bordermatrix*` - adapted from the manual "Math mode" by Herbert Voss that provides the border at bottom and right instead
- `\qbordermatrix` - Quadri-border matrix, you can select any combination of the four borders to put outside of the matrix

The `\qbordermatrix` macro takes the syntax of the following

     \qbordermatrix[#1]{#2}{
        a11 & a12 & a13 & a14 \\
        a21 & a22 & a23 & a24 \\
        a31 & a32 & a33 & a34
     }

The optional parameter #1 provides two characters as the matrix's left and
right delimiters. The parameter #2 provides a subset of "n", "s", "e", "w"
to tell which border should be outside of the matrix. Then the matrix is
provided in the last curly bracket.

In this sense, `\bordermatrix` is same as `\qbordermatrix{nw}` and
`\bordermatrix*` is same as `\qbordermatrix{se}`.

Compared to the Knuth's version, the matrices constructed by this package
has the following properties

1. The row height is determined dynamically. Thus if the border row is
   tall, e.g. a display fraction, the bracket is placed in the correct
   size.
2. The matrix is aligned at the middle of the bracket, regardless the
   heights of the matrix or the border rows
3. Different matrix delimiters are allowed, as long as they can fit into
   the `\left` and `\right` pairs in equations
4. The output is in a `vbox` and the "canva" covers exactly the matrix

Also the spacing around the matrix is a bit tight.

----

Originally I put it up at Google code and forgot it since then: https://code.google.com/archive/p/qbordermatrix/
Now migrated to GitHub for future management.
