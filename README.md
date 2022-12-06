# :sunflower: :deciduous_tree: :tulip: :blossom: Welcome to my PL garden :rose: :seedling: :hibiscus: :herb:


## What I am growing now :seedling:

### [Glask](https://github.com/glask/glask) :blossom:

I am working on a new exciting thing! It is a small programming language inspired by Haskell. It has type classes, higher-rank polymorphism, row polymorphism and other interesting features.

### [Lambdulus](https://github.com/lambdulus/frontend) :evergreen_tree:

Lambdulus is a tool for learning λ-calculus interactively. It runs localy in any modern browser and enables you to experience λ-calculus as a programming language.

![Screenshot of the part of the Lambdulus web interface](./imgs/lambdulus-frontend-fact.png)


----

## What I have grown :herb: :evergreen_tree:

### [Frea](https://github.com/lambduli/frea) - Small programming language with HM type inference, higher kinded types, and lazy evaluation

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


### [Monolog](https://github.com/lambduli/monolog) - Small logic programming language inspired by Prolog

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


### [SJS](https://github.com/lambduli/sjs) - Very simple compiler from Lisp-inspired programming language targetting JS

```lisp
  (define fact (n)
    (if (or (= n 0) (= n 1))
      1
      (* n (fact (- n 1)))
    )
  )

  (fact 5)
```


### [FeenyML](https://github.com/lambduli/FeenyML) - Interpreter and (incomplete) VM for small programming language inspired by Feeny and ML

```ml
  function fact (num) ->
    if num == 0
    then 1
    else num * fact(num - 1);

  fact(5)
```


### [Lambda-pie](https://github.com/lambduli/lambda-pie) - Three better simple REPLs for `λ->`, `λ2`, and `λΠ`

```
  λ-> >> assume (id :: T -> T) (T :: *) (a :: T) (b :: T)
  λ-> >> id a
        (id a) :: T
  λ-> >> id b
        (id b) :: T
```


### [Lambdas](https://github.com/lambduli/lambdas) - Three simple REPLs for `λ`, `λ->`, and `λ2`
<!--
```
  [enter λ2 expression]
  λ2 >> (\ a : forall A . A -> A -> A . a) (/ B . (\t : B . (\f : B . t)))
        (λ a : (forall A . A -> A -> A) . a) (Λ B . (λ t : B . (λ f : B . t))) :: (forall A . A -> A -> A)
```
-->

### [DFSM-DSL](https://github.com/lambduli/dfsm-dsl) - JS DSL for implementing Deterministic Finite State Machines
<!--
```javascript
  let factorial = dfsm`
  state default INIT

  compute
    INIT -> ${(state, num) => num === 0 ? '1' : `${num}`}
      ${(state, num) => num === 0 ? undefined : factorial.compute(num - 1)} .

  compute
    ${state => state === 'INIT' ? 'NO' : state} ->
      ${(state, num) => num === 0 ? state : `${Number(state) * num}`}
      
      ${(state, num) => num === 0 ? state : factorial.compute(num - 1)} .`

  factorial.compute(5)
```
-->
