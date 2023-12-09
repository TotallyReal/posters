### Introduction

The simple continued fraction expansion is a central and important
mathematical tool used in many areas in mathematics and outside it.
There are many interesting properties that can be extracted from these
expansions, and in particular properties which show how "close" a number
is to being rational. For example, some interesting expansions for the
golden ratio $\varphi$, $\sqrt{2}$ and $e$ are 
```math
\begin{aligned}
\varphi & :=\frac{1+\sqrt{5}}{2}=1+\frac{1}{1+\frac{1}{1+\frac{1}{1+\frac{1}{1+\frac{1}{1+\begin{aligned}\ddots\end{aligned}
}}}}},\quad\sqrt{2}=1+\frac{1}{2+\frac{1}{2+\frac{1}{2+\frac{1}{2+\frac{1}{2+\begin{aligned}\ddots\end{aligned}
}}}}},\quad e=2+\frac{1}{1+\frac{1}{2+\frac{1}{1+\frac{1}{1+\frac{1}{4+\frac{1}{1+\begin{aligned}\ddots\end{aligned}
}}}}}}.
\end{aligned}
```
 This type of expansions have the extra property that
they are very easy to write. For example, in $\varphi$ and $\sqrt{2}-1$
the coefficients are constant (1 and 2 respectively), and generally in
any algebraic number of degree 2 the coefficients will be eventually
periodic (and we go over some of these details in ). On the other hand
$e-2$ is not algebraic, but still the coefficients are in essence
periodic: they are 3-periodic where the coefficients in the $k$-th
period are $\left(1,2k,1\right)$.

However, in general this is far from true, even for well known and
useful constants, e.g. for $\pi$ we have

```math
\pi=3+\frac{1}{7+\frac{1}{15+\frac{1}{1+\frac{1}{292+\frac{1}{1+\frac{1}{1+\frac{1}{1+\frac{1}{2+\begin{aligned}\ddots\end{aligned}
}}}}}}}}.
```
 The coefficients in the expansion don't seem to have any
simple pattern that we can recognize, thus making it harder to study
$\pi$ through this expansion.

The goal of this paper is to study a close relative of the simple
continued fractions called the **polynomial continued fraction**. In
this new expansion, we don't restrict the numerators to be $1$'s as in
the simple continued fraction version, however we do require both the
numerators and denominators to be polynomials. For example, $\pi$ has
this much simpler polynomial continued fraction expansion:


```math
\pi+3=6+\frac{1^{2}}{6+\frac{2^{2}}{6+\frac{3^{2}}{6+\frac{4^{2}}{6+\begin{aligned}\ddots\end{aligned}
}}}}.
```


This new type of expansion loses some of the advantages of the simple
continued fraction expansion, and their direct relations to
irrationality, but in return we gain many more expansions, which can be
much easier to work with, thus may lead to many interesting new results.
In particular, the polynomial continued fractions are closely related to
recurrence relations with polynomial coefficients. This type of
polynomial recurrence was one of the key ingredients used by Apéry to
show the irrationality of $\zeta\left(3\right)$
[@apery_irrationalite_1979; @van_der_poorten_proof_1979].

One of the simplest way to construct polynomial continued fractions was
given by Euler, which found a way to convert many interesting infinite
sums presentations into polynomial continued fractions (see for
details). Our main result in this paper is describing the other
direction, namely finding simple conditions for when a polynomial
continued fraction can be converted back into an infinite sum. We call
this family the **Euler continued fractions**. Using the notation

```math
\mathbb{K}_{1}^{\infty}\frac{b_{i}}{a_{i}}:=\frac{b_{1}}{a_{1}+\cfrac{b_{2}}{a_{2}+\cfrac{b_{3}}{a_{3}+\ddots}}},
```

we have the following:

::: {#thm:recurrence-roots .thm}
** 1** (***Euler continued fractions***). *Let
$h_{1},h_{2},f:\mathbb{C}\to\mathbb{C}$ be any functions, and define
$a,b:\mathbb{C}\to\mathbb{C}$ such that 
```math
\begin{aligned}
b\left(x\right) & =-h_{1}\left(x\right)h_{2}\left(x\right)\\
f\left(x\right)a\left(x\right) & =f\left(x-1\right)h_{1}\left(x\right)+f\left(x+1\right)h_{2}\left(x+1\right).
\end{aligned}
```
 Then

```math
\mathbb{K}_{1}^{n}\frac{b\left(i\right)}{a\left(i\right)}=\frac{f\left(1\right)h_{2}\left(1\right)}{f\left(0\right)}\left(\frac{1}{\sum_{k=0}^{n}\frac{f\left(0\right)f\left(1\right)}{f\left(k\right)f\left(k+1\right)}\prod_{i=1}^{k}\left(\frac{h_{1}\left(i\right)}{h_{2}\left(i+1\right)}\right)}-1\right).
```
*
:::

::: rem
* 2*. Special cases of these continued fractions appear in several
places (in particular, see for example
[@brier_note_2022; @bowman_polynomial_2018; @cohen_elementary_2022]),
though we did not see this exact formulation in the literature.
:::

In general, given polynomials $b\left(x\right),a\left(x\right)$, it is
not obvious if and how to find polynomial
$h_{1}\left(x\right),h_{2}\left(x\right),f\left(x\right)$ which satisfy
the conditions in . Assuming we know how to find all decompositions of
$b\left(x\right)$, this problem is easy to solve in the "trivial" case
when $f\equiv1$. More generally, if we know the degree
$d_{f}=\deg\left(f\right)$, then finding if there is a solution to

```math
f\left(x\right)a\left(x\right)=f\left(x-1\right)h_{1}\left(x\right)+f\left(x+1\right)h_{2}\left(x+1\right)
```

given $a\left(x\right),h_{1}\left(x\right),h_{2}\left(x\right)$ is just
a system of linear equations which is easy to solve. Our second result
is an algorithm which finds all the possible degree $d_{f}$ thus
allowing to give a full algorithm checking whether a polynomial
continued fraction is in the Euler family (given that we know how to
decompose $b\left(x\right)$). We describe this algorithm in , and in
particular in , and we also provide a python program for this algorithm
in [@ramanujan_machine_research_group_ramanujan_2023].

Finally, we describe a more general framework for the polynomial
continued fractions in , by moving to general polynomial matrices. This
led us eventually to a new structure, which we call the **conservative
matrix field**, used to combine many polynomial continued fractions
together in order to study their limits (e.g. if they are irrational or
not). This conservative matrix field can be used to reprove and further
understand Apéry's original proof of irrationality of
$\zeta\left(3\right)$, and we investigate this structure in a later
paper.

### []{#sec:Generalized-continued-fractions label="sec:Generalized-continued-fractions"}The polynomial continued fraction

#### []{#subsec:The-definitions label="subsec:The-definitions"}Definitions

We start with a generalization of the simple continued fractions, which
unsurprisingly, is called generalized continued fractions. These can be
defined over any topological field, though here for simplicity we focus
on the complex field with its standard Euclidean metric, and more
specifically when the numerators and denominators are integers.

::: defn
** 3** (**(Generalized) continued fractions**). Let $a_{n},b_{n}$ be a
sequence of complex numbers. We will write

```math
a_{0}+\mathbb{K}_{1}^{n}\frac{b_{i}}{a_{i}}:=a_{0}+\cfrac{b_{1}}{a_{1}+\cfrac{b_{2}}{a_{2}+\cfrac{b_{3}}{\ddots+\cfrac{b_{n}}{a_{n}+0}}}}\in\mathbb{C}\cup\left\{ \infty\right\} ,
```

and if the limit as $n\to\infty$ exists, we also will write

```math
a_{0}+\mathbb{K}_{1}^{\infty}\frac{b_{i}}{a_{i}}:={\displaystyle \lim_{n\to\infty}}\left(a_{0}+\mathbb{K}_{1}^{n}\frac{b_{i}}{a_{i}}\right).
```


We call this type of expansion (both finite and infinite) a **continued
fraction expansion.** In case that
$a_{0}+\mathbb{K}_{1}^{\infty}\frac{b_{i}}{a_{i}}$ exists, we call the
finite part $a_{0}+\mathbb{K}_{1}^{n-1}\frac{b_{i}}{a_{i}}$ the **$n$-th
convergents** for that expansion.

A continued fraction is called **simple continued fraction**, if
$b_{i}=1$ for all $i$, $a_{0}\in\mathbb{Z}$ and
$1\leq a_{i}\in\mathbb{Z}$ are positive integers for $i\geq1$.

A continued fraction is called **polynomial continued fraction**, if
$b_{i}=b\left(i\right),\;a_{i}=a\left(i\right)$ for some polynomials
$a\left(x\right),b\left(x\right)\in\mathbb{C}\left[x\right]$ and all
$i\geq1$.
:::

::: rem
* 4*. In these notes, when talking about **simple continued fractions**
we will always add the "**simple**" adjective, unlike in most of the
literature, where they are only called **continued fractions**.
:::

Simple continued fraction expansion is one of the main and basic tools
used in number theory when studying rational approximations of numbers
(for more details, see chapter 3 in [@einsiedler_ergodic_2013]). The
coefficients $a_{i}$ in that expansion can be found using a generalized
Euclidean division algorithm, and it is well known that a number is
rational if and only if its simple continued fraction expansion is
finite. However, while we have an algorithm to find the (almost) unique
expansion, in general they can be very complicated without any known
patterns, even for "nice" numbers, for example:


```math
\pi=[3;7,15,1,292,1,1,1,2,1,3,1,14,2,1,1,2,2,2,2,1,84,...]=3+\cfrac{1}{7+\cfrac{1}{15+\cfrac{1}{1+\ddots}}}.
```


When moving to generalized continued fractions, even when we assume that
both $a_{i}$ and $b_{i}$ are integers, we lose the uniqueness property,
and the rational if and only if finite property. What we gain in return
are more presentations for each number, where some of them can be much
simpler to use. For example, $\pi$ can be written as

```math
\pi=3+\mathbb{K}_{1}^{\infty}\frac{\left(2n-1\right)^{2}}{6}.
```
 We
want to study these presentations, and (hopefully) use them to show
interesting properties, e.g. prove irrationality for certain numbers.
