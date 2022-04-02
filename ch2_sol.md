# Chapter 2

## Exercise 2.1
### Problem
Which one of these objects can be represented by a binary string?

a. An integer $x$.

b. An undirected graph $G$.

c. A directed graph $H$.

d. All of the above.

### Solution
The answer should be d. All the representations could be found in chapter 2.

## Exercise 2.2 (Binary representation)
### Problem
a. Prove that the function $NtS:\N \rightarrow \{0,1\}^*$ of the binary representation defined in [ntseq](){.eqref} satisfies that for every $n\in \N$, if $x = NtS(n)$ then $|x| =1+\max(0,\floor{\log_2 n})$ and $x_i = \floor{x/2^{\floor{\log_2 n}-i}} \mod 2$.

b. Prove that $NtS$ is a one to one function by coming up with a function $StN:\{0,1\}^* \rightarrow \N$ such that $StN(NtS(n))=n$ for every $n\in \N$.
### Solution

## Exercise 2.3 (More compact than ASCII representation)
### Problem
The ASCII encoding can be used to encode a string of $n$ English letters as a $7n$ bit binary string, but in this exercise, we ask about finding a more compact representation for strings of English lowercase letters.

1. Prove that there exists a representation scheme $(E,D)$ for strings over the 26-letter alphabet $\{ a, b,c,\ldots,z \}$ as binary strings such that for every $n>0$ and length-$n$ string $x \in \{ a,b,\ldots,z \}^n$, the representation $E(x)$ is a binary string of length at most  $4.8n+1000$. In other words, prove that for every $n$, there exists a one-to-one function $E:\{a,b,\ldots, z\}^n \rightarrow \{0,1\}^{\lfloor 4.8n +1000 \rfloor}$.

2. Prove that there exists _no_ representation scheme for strings over the alphabet $\{ a, b,\ldots,z \}$ as binary strings such that for every length-$n$ string $x \in \{ a,b,\ldots, z\}^n$, the representation $E(x)$ is a binary string of length  $\lfloor 4.6n+1000 \rfloor$. In other words, prove that there exists some $n>0$ such that there is no one-to-one function $E:\{a,b,\ldots,z \}^n \rightarrow \{0,1\}^{\lfloor 4.6n + 1000 \rfloor}$.

3. Python's `bz2.compress` function is a mapping from strings to strings,  which uses the _lossless_ (and hence _one to one_) [bzip2](https://en.wikipedia.org/wiki/Bzip2) algorithm for compression.  After converting to lowercase, and truncating spaces and numbers, the text of Tolstoy's "War and Peace" contains $n=2,517,262$. Yet, if we run `bz2.compress` on the string of the text of "War and Peace" we get a string of length $k=6,274,768$ bits, which is only $2.49n$ (and in particular much smaller than $4.6n$). Explain why this does not contradict your answer to the previous question.

4. Interestingly, if we try to apply `bz2.compress` on a _random_ string, we get much worse performance. In my experiments, I got a ratio of about $4.78$ between the number of bits in the output and the number of characters in the input.  However, one could imagine that one could do better and that there exists a company called "Pied Piper" with an algorithm that can losslessly compress a string of $n$ random lowercase letters to fewer than $4.6n$ bits.^[Actually that particular fictional company uses a metric that focuses more on compression _speed_ then _ratio_, see [here](https://blogs.dropbox.com/tech/2016/06/lossless-compression-with-brotli/) and [here](https://www.jefftk.com/p/weissman-scores-useful).] Show that this is not the case by proving that for _every_ $n>100$ and one to one function $Encode:\{a,\ldots,z\}^{n} \rightarrow \{0,1\}^*$, if we let $Z$ be the random variable  $|Encode(x)|$ (i.e., the length of $Encode(x)$) for $x$ chosen uniformly at random from the set $\{a,\ldots,z\}^n$, then the expected value of $Z$ is at least $4.6n$.

## Exercise 2.4 (Representing graphs: upper bound)
### Problem
Show that there is a string representation of directed graphs with vertex set $[n]$ and degree at most $10$ that uses at most $1000 n\log n$ bits. More formally, show the following: Suppose we define for every $n\in\mathbb{N}$, the set $G_n$ as the set containing all directed graphs (with no self loops) over the vertex set $[n]$ where every vertex has degree at most $10$. Then, prove that for every sufficiently large $n$, there exists a one-to-one function $E:G_n \rightarrow \{0,1\}^{\lfloor 1000 n \log n \rfloor}$.

## Exercise 2.5 (Representing graphs: lower bound)
### Problem
1. Define $S_n$ to be the set of one-to-one and onto functions mapping $[n]$ to $[n]$. Prove that there is a one-to-one mapping from $S_n$ to $G_{2n}$, where $G_{2n}$ is the set defined in [representinggraphsex](){.ref} above.

2. In this question you will show that one cannot improve the representation of [representinggraphsex](){.ref} to length $o(n \log n)$. Specifically, prove for every sufficiently large  $n\in \mathbb{N}$ there is _no_ one-to-one function $E:G_n \rightarrow \{0,1\}^{\lfloor 0.001 n \log n \rfloor +1000}$.


## Exercise 2.6 (Multiplying in different representation)
### Problem
Recall that the grade-school algorithm for multiplying two numbers requires $O(n^2)$ operations. Suppose that instead of using decimal representation, we use one of the following representations $R(x)$ to represent a number $x$ between $0$ and $10^n-1$. For which one of these representations you can still multiply the numbers in $O(n^2)$ operations?

a. The standard binary representation: $B(x)=(x_0,\ldots,x_{k})$ where $x = \sum_{i=0}^{k} x_i 2^i$ and $k$ is the largest number s.t. $x \geq 2^k$.

b. The reverse binary representation: $B(x) = (x_{k},\ldots,x_0)$ where $x_i$ is defined as above for $i=0,\ldots,k-1$. \

c. Binary coded decimal representation: $B(x)=(y_0,\ldots,y_{n-1})$ where $y_i \in \{0,1\}^4$ represents the $i^{th}$ decimal digit of $x$ mapping $0$ to $0000$, $1$ to $0001$, $2$ to $0010$, etc. (i.e. $9$ maps to $1001$)

d.  All of the above.

## Exercise 2.7
### Problem
Suppose that $R:\N \rightarrow \{0,1\}^*$ corresponds to representing a number $x$ as a string of $x$ $1$'s, (e.g., $R(4)=1111$, $R(7)=1111111$, etc.).
If $x,y$ are numbers between $0$ and $10^n -1$, can we still multiply $x$ and $y$ using $O(n^2)$ operations if we are given them in the representation $R(\cdot)$?

## Exercise 2.8
### Problem
Recall that if $F$ is a one-to-one and onto function mapping elements of a finite set $U$ into a finite set $V$ then the sizes of $U$ and $V$ are the same. Let $B:\N\rightarrow\{0,1\}^*$ be the function such that for every $x\in\N$, $B(x)$ is the binary representation of $x$.

1. Prove that $x < 2^k$ if and only if $|B(x)| \leq k$.

2. Use 1. to compute the size of the set $\{ y \in \{0,1\}^* : |y| \leq k \}$ where $|y|$ denotes the length of the string $y$.

3. Use 1. and 2. to prove that $2^k-1 = 1 + 2 + 4+ \cdots + 2^{k-1}$.

## Exercise 2.9 (Prefix-free encoding of tuples)
### Problem
Suppose that $F:\N\rightarrow\{0,1\}^*$ is a one-to-one function that is _prefix-free_ in the sense that there is no $a\neq b$ s.t.  $F(a)$ is a prefix of $F(b)$.

a. Prove that $F_2:\N\times \N \rightarrow \{0,1\}^*$, defined as $F_2(a,b) = F(a)F(b)$ (i.e., the concatenation of $F(a)$ and $F(b)$) is a one-to-one function.

b. Prove that $F_*:\N^*\rightarrow\{0,1\}^*$ defined as $F_*(a_1,\ldots,a_k) = F(a_1)\cdots F(a_k)$ is a one-to-one function, where $\N^*$ denotes the set of all finite-length lists of natural numbers.

## Exercise 2.10 (More efficient prefix-free transformation)
### Problem
Suppose that $F:O\rightarrow\{0,1\}^*$ is some (not necessarily prefix-free) representation of the objects in the set $O$, and $G:\N\rightarrow\{0,1\}^*$ is a prefix-free representation of the natural numbers.  Define $F'(o)=G(|F(o)|)F(o)$ (i.e., the concatenation of the representation of the length $F(o)$ and $F(o)$).

a. Prove that $F'$ is a prefix-free representation of $O$.

b. Show that we can transform any representation to a prefix-free one by a modification that takes a $k$ bit string into a string of length at most $k+O(\log k)$.

c. Show that we can transform any representation to a prefix-free one by a modification that takes a $k$ bit string into a string of length at most $k+ \log k + O(\log\log k)$.^[Hint: Think recursively how to represent the length of the string.]

## Exercise 2.11 (Kraft's Inequality)
### Problem
Suppose that $S \subseteq \{0,1\}^*$ is some finite prefix-free set, and let $n$ some number larger than $\max \{ |x| : x\in X \}$.

a. For every $x\in S$, let $L(x) \subseteq \{0,1\}^n$ denote all the length-$n$ strings whose first $k$ bits are $x_0,\ldots,x_{k-1}$. Prove that __(1)__ $|L(x)|=2^{n-|x|}$ and __(2)__ For every distinct $x,x' \in S$,  $L(x)$ is disjoint from $L(x')$.

b. Prove that $\sum_{x\in S}2^{-|x|} \leq 1$. (_Hint:_ first show that $\sum_{x \in S} |L(x)| \leq 2^n$.) 

c. Prove that there is no prefix-free encoding of strings with less than logarithmic overhead. That is, prove that there is no function $PF:\{0,1\}^* \rightarrow \{0,1\}^*$ s.t. $|PF(x)| \leq |x|+0.9\log |x|$ for every sufficiently large $x\in \{0,1\}^*$ and such that the set $\{ PF(x) : x\in \{0,1\}^* \}$ is prefix-free. The factor $0.9$ is arbitrary; all that matters is that it is less than $1$.

## Exercise 2.12 (Composition of one-to-one functions)
### Problem
Prove that for every two one-to-one functions $F:S \rightarrow T$ and $G:T \rightarrow U$, the function $H:S \rightarrow U$ defined as $H(x)=G(F(x))$ is one to one.

## Exercise 2.13 (Natural numbers and strings)
### Problem
1. We have shown that the natural numbers can be represented as strings. Prove that the other direction holds as well: that there is a one-to-one map $StN:\{0,1\}^* \rightarrow \N$. ($StN$ stands for "strings to numbers.")

2. Recall that Cantor proved that there is no one-to-one map $RtN:\R \rightarrow \N$. Show that Cantor's result implies [cantorthm](){.ref}.

## Exercise 2.14 (Map lists of integers to a number)
### Problem
Recall that for every set $S$, the set $S^*$ is defined as the set of all finite sequences of members of $S$ (i.e., $S^* = \{ (x_0,\ldots,x_{n-1}) \;|\; n\in\mathbb{N} \;,\; \forall_{i\in [n]} x_i \in S \}$ ). Prove that there is a one-one-map from $\mathbb{Z}^*$ to $\mathbb{N}$ where $\mathbb{Z}$ is the set of $\{ \ldots, -3 , -2 , -1,0,+1,+2,+3,\ldots \}$ of all integers.
