# Past Projects

## :school: [Lambdulus](https://github.com/lambdulus/frontend) :evergreen_tree:

Lambdulus is a tool for learning λ-calculus interactively.
It runs locally in any modern browser and enables you to experience λ-calculus as a programming language.

It's being used at FIT CTU in Prague for teaching λ-calculus in a course on programming paradigms.

<!-- ![Screenshot of the part of the Lambdulus web interface](./imgs/lambdulus-frontend-fact.png) -->


## [Resin](https://github.com/lambduli/resin) :hibiscus: :tulip:

Resin is a small automated theorem prover for _First Order Classical Logic_ built on *resolution*.

It's another step on my journey through the topic of formal reasoning and implementing theorem provers and proof assistants.
It is not my goal to make it real-world applicable at all. I just want to explore the concepts related to the _resolution_ and learn more about logic.


```
constants: zero .

aliases : 0 = zero
        , 1 = suc(0) .

axioms: ∀ n Plus(0, n, n)
      , ∀ n m r Plus(n, m, r) ==> Plus(suc(n), m, suc(r))

      , ∀ n Times(0, n, 0)
      , ∀ n m r a [Times(n, m, r) ∧ Plus(r, m, a) ==> Times(suc(n), m, a)]

      , Fact(0, 1)
      , ∀ n pr r [Fact(n, pr) ∧ Times(suc(n), pr, r) ==> Fact(suc(n), r)]
      .

theorem fact-0-is-1: Fact(0, 1) .

theorem fact-1-is-1 : Fact(1, 1) .

theorem exists-fact-for-1 : ∃ n Fact(n, 1) .
```


## [Plover](https://github.com/lambduli/plover) :rose:

Plover is a small automated theorem prover based on a logic language like *Prolog*.
The main idea is to replace *Minilog's* depth-first search strategy with a complete one.

It serves as the first step on my journey to study the topic of formal reasoning and automated and interactive theorem provers and assistants.
It's as small as _Minilog_.

The main difference the complete search strategy makes is that the language can productively answer queries like `nat(A).` for a knowledge base like the following:

```prolog
nat(s(N)) :- nat(N).
nat(z).
```


## [Minilog](https://github.com/lambduli/minilog) :cherry_blossom:

Minilog is an implementation of a small logic programming language.
The primary purpose of it is to present a simple abstract machine that can be easily implemented in any language and can serve as an aid when making the intuition about how such a language works.

I have designed the abstract machine and written a [description](https://github.com/lambduli/minilog/blob/main/WRITEUP.md) of it for (not only) my students to learn about how such a language works.
It is meant to inspire and offer a starting point to them should they decide to implement a small subset of Prolog as their course project.

_Minilog_ is not the first project in a line of logic languages.
In the past, I've implemented a small logic language [Monolog](https://github.com/lambduli/monolog).
But back then, I didn't know how to implement the _unification_ in a sensible way.
So, while the _Minilog_ implements unification according to _Martelli and Montanari_,
the first project keeps around sort of a _unification context_ making it very impractical and inefficient.


```prolog
plus(z, N, N).
plus(s(N), M, s(R)) :- plus(N, M, R).

times(z, _, z).
times(s(N), M, A) :- times(N, M, R), plus(R, M, A).

fact(z, s(z)).
fact(s(N), R) :- fact(N, PR), times(s(N), PR, R).
```


## [Frea](https://github.com/lambduli/frea) :chestnut:

Small programming language with HM type inference, higher-kinded types, and lazy evaluation.
Implemented as an AST interpreter in Haskell.

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


## [Lambda-pie](https://github.com/lambduli/lambda-pie) :palm_tree:

Three better simple REPLs for `λ->`, `λ2`, and `λΠ`.


```
λ-> >> assume (id :: T -> T) (T :: *) (a :: T) (b :: T)
λ-> >> id a
      (id a) :: T
λ-> >> id b
      (id b) :: T
```


## [Lambdas](https://github.com/lambduli/lambdas) :ear_of_rice:

Three simple REPLs for `λ`, `λ->`, and `λ2`.
