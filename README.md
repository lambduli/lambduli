# :sunflower: :deciduous_tree: :tulip: :blossom: Welcome to my PL garden :rose: :seedling: :hibiscus: :herb:


## What I am growing now :seedling:


### [Glask](https://github.com/lambduli/glask) :blossom:

I am working on a new exciting thing! It is a small programming language inspired by Haskell. It has type classes, higher-rank polymorphism, row polymorphism and other interesting features.



## What I have grown :herb: :evergreen_tree:

### [Lambdulus](https://github.com/lambdulus/frontend) :evergreen_tree:

Lambdulus is a tool for learning λ-calculus interactively. It runs localy in any modern browser and enables you to experience λ-calculus as a programming language.

![Screenshot of the part of the Lambdulus web interface](./imgs/lambdulus-frontend-fact.png)


### [Minilog](https://github.com/lambduli/minilog) :cherry_blossom:

Minilog is an implementation of a small relational programming language. The main purpose of it is to present a simple abstract machine that can be easily implemented in any language and can serve as an aid when making the intuition about how such a language works.
```prolog
  plus(z, N, N).
  plus(s(N), M, s(R)) :- plus(N, M, R).

  times(z, _, z).
  times(s(N), M, A) :- times(N, M, R), plus(R, M, A).

  fact(z, s(z)).
  fact(s(N), R) :- fact(N, PR), times(s(N), PR, R).
```


### [Frea](https://github.com/lambduli/frea)

Small programming language with HM type inference, higher kinded types, and lazy evaluation.
Implemented as an AST interpreter in Haskell.

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


### [Monolog](https://github.com/lambduli/monolog)

Small logic programming language inspired by Prolog.
Implemented as an AST interpreter in Ruby.

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


### [SJS](https://github.com/lambduli/sjs)

Very simple compiler from a Lisp-inspired programming language targetting JS.
Implemented as a parser and a trivial code-gen in Scala.

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


### [DFSM-DSL](https://github.com/lambduli/dfsm-dsl)

JS DSL for implementing Deterministic Finite State Machines.
