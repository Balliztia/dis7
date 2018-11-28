## Programming with Recursion and without Recursion

#### Relationship
- Recursion: address one big problem with several subproblems with a same structure.
- Function stack: last call, first return
  - call f()
  - f() call f_1()
  - f_1() call f_2()
  - ......
  - f_k-1() call f_k()
  - f_k() return
  - f_k-1 return
  - ......
  - f_2() return
  - f_1() return
  - f() return
- Actually, stack is the bridge from recursion to non-recursion

#### Solve problem by Recursion
- Input : subproblem, same structure
- Output : used in previous level
- When to call itself
- When to return or basic case

#### Solve problem by Stack
- Iteration
- What to store in the Stack
- When and what to push
- When to pop
