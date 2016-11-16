---
layout: post
title: "Uncomputable binary relations"
fbcomments: yes
tags:
- math
- computability
- model-theory
---

Consider a binary relation $$R$$ on a countable set $$S$$, i.e. $$R \subseteq S \times S$$.
Equivalently, this is a directed graph where $$S$$ is the set of vertices and $$R$$ is the edge relation.
We might be interested in whether $$R$$ is *computable*: given vertices $$x, y \in S$$, is it decidable whether $$xRy$$?

However, this doesn't make sense, because we haven't picked a representation of the elements of $$S$$ -- we need to first assign elements of $$S$$ to natural numbers (alternatively, to binary strings). Given any bijection $$\sigma: S \to \mathbb{N}$$, we can *then* ask if $$\sigma(R)$$ ($$\sigma$$ applied to each coordinate of each pair in the relation) is a computable relation on $$\mathbb{N} \times \mathbb{N}$$.

We might split all binary relations / directed graphs on $$S$$, then, into three types:

1. *Unconditionally computable:* for any bijection $$\sigma: S \to \mathbb{N}$$,
   $$\sigma(R)$$ is computable.

2. *Conditionally computable:* there exist bijections $$\sigma_1, \sigma_2: S \to \mathbb{N}$$ such that $$\sigma_1(R)$$ is computable but $$\sigma_2(R)$$ is not.

3. *Uncomputable:* for any bijection $$\sigma: S \to \mathbb{N}$$, $$\sigma(R)$$ is uncomputable.

Some examples should make this classification more clear:

- Suppose $$(S,R)$$ is a directed graph with a specific vertex $$a \in S$$, and

  $$R = \{(a,y) \mid y \in S\}.$$

  This is a relation of type (1), because no matter how we represent vertices as binary strings, $$a$$ is some particular string, and we can decide if $$xRy$$ by just checking if $$x = a$$.

- Let $$S = \mathbb{N}$$, with

  $$R = \{(x,0) \mid x \text{ is even}\} \cup \{(x,1) \mid x \text{ is odd}\}.$$

  If $$\sigma$$ is the identity function $$\mathbb{N} \to \mathbb{N}$$, then this is certainly computable. However, we can
  instead have $$\sigma$$ send all odd numbers to halting turing machines, and even numbers to
  non-halting turing machines (where turing machines are represented as natural numbers in a
  standard way). If so, then $$R$$ becomes uncomputable. So this relation is of type (2).

- Let $$S = \mathbb{N}$$ again, with

  $$R = \{(x,y) \mid x < y\}.$$

  This is again computable if $$\sigma$$ is the identity bijection, because $$<$$ is a computable relation on natural numbers. But once again using a general bijection we can cause it to be uncomputable. For example, we can arrange so that $$(n,n+1) \in \sigma(R)$$ for every odd $$n$$ representing a halting Turing machine, and $$(n+1,n) \in \sigma(R)$$ for every odd $$n$$ representing a non-halting Turing machine. So this is another example of type (2).

I'm told I'm not supposed to put exercises in a blog post, but here I go:

**Exercise.** Construct a relation of type (3).

(*Hint:* One approach is for $$R$$ to consist of a cycle of length $$BB(n)$$, for each natural number $$n$$, where $$BB$$ is the busy beaver function. Then you have to prove that this works.)

### Some observations

There are only countably many relations of type (1), and they are of a very particular kind.
Here is a classification theorem:

**Theorem.** $$R$$ has type (1) if and only if there exists a finite subset $$S_0 \subseteq S$$ such that for all $$x \in S$$ and for all $$y, y' \in S \setminus S_0$$,
$$xRy$$ if and only if $$xRy'$$ and $$yRx$$ if and only if $$y'Rx$$.
In other words, all vertices outside of $$S_0$$ are indistinguishable from each other;
any vertex is either connected to all of $$S \setminus S_0$$, or none of $$S \setminus S_0$$.

An equivalent way of saying the above condition is that there is a
quantifier-free formula $$\varphi(x,y)$$ over the language of equality and allowing constants from
$$S$$, that defines $$R$$. I.e., $$xRy$$ if and only if $$\varphi(x,y)$$.

On the other hand, there are uncountably many relations of type (2) (for silly reasons), but there are only countably many *non-isomorphic* relations of type (2).
Since [the number of non-isomorphic countable graphs is $$2^{\aleph_0}$$](http://math.stackexchange.com/questions/27398/how-many-countable-graphs-are-there), this means "most" relations are of type (3).

Although we can't construct one explicitly,
it turns out that [any countable model of ZFC is of type (3)](http://mathoverflow.net/questions/12426/is-there-a-computable-model-of-zfc).
(In this case $$S$$ is the underlying set of the model, and $$R$$ is the "is an element of" binary relation.)
In contrast, the standard model of Peano Arithmetic is entirely computable -- successor, addition, and multiplication are all computable functions on the natural numbers.
