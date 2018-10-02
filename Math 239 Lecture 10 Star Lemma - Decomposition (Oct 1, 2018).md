# Math 239 - Lecture 11 - Concatenation - (Block) Decomposition

## Review:

### Concatenation:
$AB = \\{ab: a \in A, bE \in B\}$ set! (not multiset) unambiguous if $\nexists {{a}_{1}},{{a}_{2}}\in A,{{b}_{1}},{{b}_{2}}\in B\text{  }{{a}_{1}}{{b}_{1}}={{a}_{2}}{{b}_{2}}$

### Star:
$A* = {E}\cup(A^1)\cup(A^2)\cup(A^3)\cup...$

### Unambiguous 
- $A^k$ unambiguous $\forall k \leq 0$
- all pairwise disjoint

### Product Lemma

If $AB$ is unambiguous then $\Phi_{AB}(x) = \Phi_{A}(x)\Phi_{B}(x)$.

### Star Lemma 

If $A*$ is unambiguous, then $\Phi_{A*}(x) = \frac{1}{1 - \Phi_A(x)}$

**Note:** we say an expression for binary strings is unambiguous if all products and stars unambiguous and unions disjoint

## Expressions for the set of all binary strings: 
Let $B$ be the set of all binary strings;

**#1:** $B = {0,1}*$ is **unambiguous**, why?

- every string is uniquely reconstructable
- alternatively, the exp. comes from a "decomposition rule"

A **decomposition rule** is a rule to decompose a string into "parts" **uniquely**.
Here the rule is: decompose where each part is a single digit

Ex: $[0][1][0][1]$

each part is in ${0,1}$, each string is formed from any # of these parts.
So we get ${0,1}*$ as the expression

**Remark:** decomposing after every 2nd digit ${00, 01, 10, 11}* {\in, 0, 1}$ is another unique rule (we won't use).
however decomposing where each part is length $1$ or $2$ is not unique (and hence is ambiguous)

### Useful unambiguous for expressions for $B$:
|Decomposition Rule | Expression|
|-------------------|-----------|
|After each 0 | $(\\{1\}*\\{0\})*, \\{1\}*$|
|After each 1 | $(\\{0\}*\\{1\} )* \\{0\}*$|
|After each block of $0$s | $\\{0\}* (\\{1\}\\{1\}*\\{0\}\\{0\}*)*\\{1\}*$|
| $1$s | $\\{1\}* (\\{0\}\\{0\}*\\{1\}\\{1\}*)*\\{1\}*$|

**Why?**

|Main parts of Decomp (used any # of times) | Final part|
|--|--|
|$\\{0, 10, 110, 1110,...\} = \\{1\}*\\{0\}$ | $\\{\in, 1, 11, 111,...\} = \\{1\}*$ |
$\\{0\}*\\{1\}$ | $\\{0\}*$|

|Beginning part | Main part | Final part |
|-----|----|---|
|(possibly empty) block of $0$s: $\\{0\}*$ | non empty block of $1$s followed by a non empty block of $0$s: $\\{1, 11, 111,...\}\\{0,00,000,...\}$|(possibly empty) block of $1$s: $\\{1\}$* |


### Finding Gen series from Block Decompositions:
the 1st rule $B = {0,1}*$ is really only useful to find $\Phi_B$.
By Star Lemma $\Phi_B(x) = \frac{1}{1 - \Phi_{\\{0,1\}(x)}} = \frac{1}{1-2x}$

One can check the other rules also give $\Phi_B(x) = \frac{1}{1 - 2x}$

Using the block decomposition rules, we can find unambiguous expresions for sets of binary strings w/ restriction parts and from there use sum/product/star lemmas to find $phi_S$

**Ex.** No blocks of exactly $4$ $1$'s:
We choose a decomposition where the restriction can be used on the parts.

Let's use after each block of $1$'s:
$B = \\{1\}*(\\{0\}\\{0\}*\\{1\}\\{1\}*)*\\{0\}*$


We modify the exp. by modifying the acceptable parts


|            | Before(all)    | After (number of blocks of ex. 4 1's)      |
|------------|----------------|--------------------------------------------|    
| Beg part   | $\\{1\}*$           | $\\{\in, 1, 11, 111, 11111,...\}$ (no 4 1's)|
| Main part  | $\\{0\}\\{0\}*\\{1\}\\{1\}*$ | $\\{0,00,...\}\\{1, 11, 111, 11111,...\}$    |
| Final part | $\\{0\}*$           |  $\\{0\}*$                                      |

$\\{E, 1, 11, 111, 11111, ...\}(\\{0\}\\{0\}*\\{1\}\\{E, 1, 11, 1111,...\})*\\{0\}* =
(\\{E,1,11,111\}\cup\\{11111\}\\{1\}*)(\\{0\}\\{0\}*\\{1\}(\\{E, 1, 11\}\cup\\{1111\}\\{1\}*)*\\{0\}*$

Exp
$(1 + x  + x^2 + x^3 + \frac{x^5}{1-x})(\frac{1}{1 - x \cdot \frac{1}{1 - x}\cdot x \cdot (1 + x + x^2 + \frac{x^4}{1 - x}}))(1/(1 - x))$

### Reminder main part is starred 

so it will show as \frac{1}{1-\Phi_{\text{Main}}} in the middle
You final expression is,
			$\Phi_{\text{Beg}}(\frac{1}{1- \Phi_{\text{Main}}})\Phi_{\text{end}}$
- it may be useful to calculate $\Phi_{\text{Beg}}$, $\Phi_{\text{Main}}$, and $\Phi_{\text{end}}$ first
