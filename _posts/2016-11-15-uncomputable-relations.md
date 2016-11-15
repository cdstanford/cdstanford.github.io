---
layout: post
title: "Uncomputable binary relations"
fbcomments: yes
---

Consider a binary relation $$R$$ on a countable set $$S$$, i.e. $$R \subseteq S \times S$$.
Equivalently, this is a directed graph with countably many vertices.
What does it mean for $$R$$ (or for the directed graph) to be "computable"?

It depends on the representation of $$S$$. In other words, we have to pick a bijection
$$\sigma: S \to \mathbb{N}$$ first, and then ask whether the corresponding relation on natural
numbers is computable.
We might split all binary relations / directed graphs on $$S$$, then, into three types:

1. *Unconditionally computable:* for any bijection $$\sigma: S \to \mathbb{N}$$,
   $$\sigma(R)$$ is computable.

2. *Conditionally computable:* there exist bijections $$\sigma_1, \sigma_2: S \to \mathbb{N}$$ such that $$\sigma_1(R)$$ is computable but $$\sigma_2(R)$$ is not.

3. *Uncomputable:* for any bijection $$\sigma: S \to \mathbb{N}$$, $$\sigma(R)$$ is uncomputable.

There are only countably many relations of type (1), and they are of a very particular kind.
Here is a classification theorem:

**Exercise.** Prove that $$R$$ has type (1) if and only if is some finite subset $$S_0 \subseteq S$$ such that for all $$x \in S$$ and for all $$y, y' \in S \setminus S_0$$,
$$xRy$$ if and only if $$xRy'$$ and $$yRx$$ if and only if $$y'Rx$$.

(An equivalent condition for (1), more meaningful but less tangible, is that there is a first-order formula using only equality and constants in $$S$$ that defines $$R$$. Given such a formula, we can take $$S_0$$ to be the set of variables occurring in that formula.)

On the other hand, there are uncountably many relations of type (2) (for silly reasons), but there are only countably many *non-isomorphic* relations of type (2).
Since [the number of non-isomorphic countable graphs is $$2^{\aleph_0}$$](http://math.stackexchange.com/questions/27398/how-many-countable-graphs-are-there), this means "most" relations are of type (3).

**Exercise.** Construct a relation of type (3).

(*Spoiler:* One idea is for $$R$$ to consist of a cycle of length $$BB(n)$$, for each natural number $$n$$, where $$BB$$ is the busy beaver function. Then prove that this works.)

Although we can't construct one explicitly,
it turns out that [any countable model of ZFC is of type (3)](http://mathoverflow.net/questions/12426/is-there-a-computable-model-of-zfc).
In contrast, the standard model of Peano Arithmetic is entirely computable -- successor, addition, and multiplication are all computable functions on the natural numbers.
