# :sunflower: :deciduous_tree: :tulip: :blossom: Welcome to my PL garden :rose: :seedling: :hibiscus: :herb:

I think type systems, type theory, logic, and formal reasoning are really interesting topics.
I like to build small programming languages, theorem provers, and other tools for learning PLT-related concepts.

I like to write about the things I learn.


## What I am growing now :seedling:


### [Glask](https://github.com/lambduli/glask) :blossom:

I am working on a new exciting thing!
It is a small programming language inspired by Haskell.
It has type classes, higher-rank polymorphism, row polymorphism and other interesting features.

I have already built a pretty large part of that as a part of my master's thesis.
At this point, I am reworking it from the ground up, formalizing the type system, and learning more about types.
I am hoping to make the project public one day.


## What I have grown :herb: :evergreen_tree:

### :school: [Lambdulus](https://github.com/lambdulus/frontend) :evergreen_tree:

Lambdulus is a tool for learning λ-calculus interactively.
It runs locally in any modern browser and enables you to experience λ-calculus as a programming language.

I have a strong appreciation for teaching tools.
This one is the first one I developed.
It's being used at FIT CTU in Prague for teaching λ-calculus in a course on programming paradigms.

<!-- ![Screenshot of the part of the Lambdulus web interface](./imgs/lambdulus-frontend-fact.png) -->


### [Minilog](https://github.com/lambduli/minilog) :cherry_blossom:

Minilog is an implementation of a small relational programming language.
The primary purpose of it is to present a simple abstract machine that can be easily implemented in any language and can serve as an aid when making the intuition about how such a language works.

I have designed the abstract machine and written a description of it for (not only) my students to learn about how such a language works.
It is meant to inspire and offer a starting point to them should they decide to implement a small subset of Prolog as their course project.

```prolog
  plus(z, N, N).
  plus(s(N), M, s(R)) :- plus(N, M, R).

  times(z, _, z).
  times(s(N), M, A) :- times(N, M, R), plus(R, M, A).

  fact(z, s(z)).
  fact(s(N), R) :- fact(N, PR), times(s(N), PR, R).
```


### [Plover](https://github.com/lambduli/plover) :rose:

Plover is an implementation of a small automated theorem prover based on a relational language.
The main idea is to replace *Minilog's* depth-first search strategy with a complete one.

It is the first stop in my journey to study the topic of formal reasoning and automated and interactive theorem provers and assistants.
It's as small as _Minilog_.

The main difference the complete search strategy makes is that the language/system can productively answer queries like `nat(A).` for a knowledge base like the following:

```prolog
  nat(s(N)) :- nat(N).
  nat(z).
```


### [Frea](https://github.com/lambduli/frea)

Small programming language with HM type inference, higher-kinded types, and lazy evaluation.
Implemented as an AST interpreter in Haskell [](https://img.shields.io/badge/Haskell-5D4F85.svg?style=for-the-badge&logo=Haskell&logoColor=white).

It's one of my first _larger_ projects. I wanted to learn about Hindley-Milner type inference and how to implement parametric polymorphism both for functions and data types. Additionally, I learned a bit about laziness.

Originally, the language used to treat recursion on terms very explicitly. There was a `fix` language construct.
Eventually, I replaced the `fix` with an implicit recursion. The type-checker first splits the definitions into groups of mutually recursive definitions and finds a topological ordering on them. This makes it possible to infer the types as polymorphic as possible.

```haskell
  module Main where

  { data Result a
      = None
      | Some a

  ; let
    { zero n = (n == 0)
    ; dec n = (n - 1)
    ; rec fact n =  if (zero n)
                    then 1
                    else (n * (fact (dec n)))
    } in (Some (fact 5))
  }
```
<!--

### [Monolog](https://github.com/lambduli/monolog)

Small logic programming language inspired by Prolog.
Implemented as an AST interpreter in Ruby.
-->
<!--
```prolog
  plus(z, N, N).
  plus(s(N), M, s(R)) :- plus(N, M, R).
  
  times(z, _, z).
  times(s(N), M, A) :- times(N, M, R), plus(R, M, A).
  
  fact(z, s(z)).
  fact(s(N), R) :- fact(N, PR), times(s(N), PR, R).

  :check

  fact(s(s(s(s(s(z))))), F)
```
-->

<!--
### [SJS](https://github.com/lambduli/sjs)

Very simple compiler from a Lisp-inspired programming language targetting JS.
Implemented as a parser and a trivial code-gen in Scala.
-->
<!--
```lisp
  (define fact (n)
    (if (or (= n 0) (= n 1))
      1
      (* n (fact (- n 1)))
    )
  )

  (fact 5)
```
-->

<!--
### [FeenyML](https://github.com/lambduli/FeenyML)

Interpreter and (incomplete) VM for a small programming language inspired by Feeny and ML.
Writen in Haskell using Alex and Happy.

```ml
  function fact (num) ->
    if num == 0
    then 1
    else num * fact(num - 1);

  fact(5)
```
-->

### [Lambda-pie](https://github.com/lambduli/lambda-pie)

Three better simple REPLs for `λ->`, `λ2`, and `λΠ` written in Haskell.

```
  λ-> >> assume (id :: T -> T) (T :: *) (a :: T) (b :: T)
  λ-> >> id a
        (id a) :: T
  λ-> >> id b
        (id b) :: T
```


### [Lambdas](https://github.com/lambduli/lambdas)

Three simple REPLs for `λ`, `λ->`, and `λ2` written in Haskell.

<!--
### [DFSM-DSL](https://github.com/lambduli/dfsm-dsl)

JS DSL for implementing Deterministic Finite State Machines.
-->
