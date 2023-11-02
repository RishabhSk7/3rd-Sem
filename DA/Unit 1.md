## Algorithm
> Shortest method to complete a process, while achieving expected output.

- Effective
- definite - clear and unambiguous
- Finite
- I/O

## RAM Model
A ram(Random access machine) model is a theoretical framework used in CS to analyze the complexity and efficiency of algorithms. It is a simplified abstract model that helps in understanding and analyzing the time and space requirements of algorithms.

It assumes that accessing memory blocks and arithmetic operations take constant time, and infinite memory for operation. 

The abstraction of the model help researchers to analyze the efficiency of an algorithm without being bogged down by constraints like computer architecture or programming language.

![[Unit 1 2023-10-09 14.13.56.excalidraw|500]]

Accumulator: Store cost of each step

```
for:
	int a=2;     #1 unit memory access
	int b=3;     #1 unit memory access
	int c=a+b;   #1 unit arithmetic operation
```

Instruction Cycle:
<ol>
	<li>Fetch Operator</li>
	<li>Fetch Operand</li>
	<li>Decode Operator</li>
	<li>Excecute</li>
	<li>Show
	<li>Save
</ol>

Examples for number of units used:

```
for (i<=n):
	<1 unit operation>
```
Cost in n units.

```
for (i<=n):
	for j<=m):
		<1 unit operation>
```
Cost is n\*m units.

## Asymptotic notation
**Subprogram**: Functions outside main function,  not independent in themselves.

Order: Size of program
![[Unit 1 2023-10-09 14.33.28.excalidraw|200]]

> t∝n

f(n) -> t

Asymptotes: Lines that meet at infinity.

In our context, "Asymptotic Notation" help us in finding the growth rate and behaviour of a function as inputs reach a certain limit usually infinity. It provides a way to understand the performance in a simplified and abstract manner, without being bogged down by things like architecture and language shortcomings, much like RAM Model.

SO it basically defines the time complexity, or running time of a algorithm.
#### Notations:
- **Big OH(O)** - Worst case. represents upper bound growth rate of a function. If a function `f(n)` is `O(g(n))` then it means that the function `f(n)` cannot grow faster than `g(n)` for sufficiently large values of n. 
   Let there be 2 functions, `f(n)` and `g(n)`, then `f(n)=O(g(n))` iff, there exists `C` and `k` such that `f(n) <= c*g(n)`, `C>=0`, `k>=0` for all `n>=k`.

- **Big Omega (Ω)**  - Best case. Represents the lower bound growth of a function. If a function `f(n)` is `Ω(g(n))`, then it means `f(n)` does not grow slower than `g(n)` for sufficiently large values of `n`.
   Let there be 2 functions, `f(n)` and `g(n)`, then `f(n)=Ω(g(n))` iff `f(n)>=Ω(g(n))`, `C>=0`, `k>=0`, `n>=k`.

- **Big Theta(Θ)** - Average case. This notation represents both an upper and a lower bound on the growth rate of a function. If a function `f(n)` is `Θ(g(n))`, it means that `f(n)` grows at the same rate as `g(n)` for sufficiently large values of n.

   Let there be 2 functions, `f(n)` and `g(n)`, then `f(n)=Θ(g(n))` iff `C₁ * g(n) ≤ f(n) ≤ C₂ * g(n)`, `C1,C2>=0`, `k>=0`, `n>=k`.

