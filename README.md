# :sunflower: :deciduous_tree: :tulip: :blossom: Welcome to my PL garden :rose: :seedling: :hibiscus: :herb:

I think type systems, type theory, logic, proof theory and formal reasoning are really interesting topics.
I build small programming languages, theorem provers, and other systems related to PLT concepts.

I sometimes write about the things I learn on [**my "blog"**:blue_book:](https://github.com/lambduli/writing).


## What I am growing now (in private) :seedling:


### [Glask](https://github.com/lambduli/glask) :blossom: :cactus:

Glask is my current, long-term project.
It is a small programming language inspired by Haskell.
It has type classes, higher-rank polymorphism, row polymorphism and other interesting features.

I have already built a pretty large part of that as a part of my master's thesis.
At this point, I am reworking it from the ground up, formalizing the type system, and learning more things.
I am hoping to make the project public one day.


### Detour :four_leaf_clover: :tulip:

Detour is a small proof-checker for _First Order Logic_ *Natural Deduction* proofs in *Fitch-style notation*.

It is a first step into the area of proof-checkers and (interactive) proof assistants.
I picked the Fitch-style notation because I find it nice to look at and it seems to fit the constraints of the text-file better.
The goal is to have a very simple proof-checker. Eventually, I want to make one that supports user-defined inductive data types/syntactic constructs, proof by induction, case analysis and maybe more.


## What I have grown :herb: :evergreen_tree:

### :school: [Lambdulus](https://github.com/lambdulus/frontend) :evergreen_tree:

Lambdulus is a tool for learning λ-calculus interactively.
It runs locally in any modern browser and enables you to experience λ-calculus as a programming language.

I have a strong appreciation for teaching tools.
This one is the first one I developed.
It's being used at FIT CTU in Prague for teaching λ-calculus in a course on programming paradigms.

<!-- ![Screenshot of the part of the Lambdulus web interface](./imgs/lambdulus-frontend-fact.png) -->


### [Resin](https://github.com/lambduli/resin) :hibiscus: :tulip:

Resin is a small automated theorem prover for _First Order Classical Logic_ built on *resolution*.

It's another step on my journey through the topic of formal reasoning and implementing theorem provers and proof assistants.
It is not my goal to make it real-world applicable at all. I just want to explore the concepts related to the _resolution_ and learn more about logic.

<details>
  <summary>Show a snippet :computer:</summary>

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
</details>

### [Plover](https://github.com/lambduli/plover) :rose:

Plover is a small automated theorem prover based on a logic language like *Prolog*.
The main idea is to replace *Minilog's* depth-first search strategy with a complete one.

It serves as the first step on my journey to study the topic of formal reasoning and automated and interactive theorem provers and assistants.
It's as small as _Minilog_.

The main difference the complete search strategy makes is that the language can productively answer queries like `nat(A).` for a knowledge base like the following:

```prolog
nat(s(N)) :- nat(N).
nat(z).
```


### [Minilog](https://github.com/lambduli/minilog) :cherry_blossom:

Minilog is an implementation of a small logic programming language.
The primary purpose of it is to present a simple abstract machine that can be easily implemented in any language and can serve as an aid when making the intuition about how such a language works.

I have designed the abstract machine and written a description of it for (not only) my students to learn about how such a language works.
It is meant to inspire and offer a starting point to them should they decide to implement a small subset of Prolog as their course project.

_Minilog_ is not the first project in a line of logic languages.
In the past, I've implemented a small logic language [Monolog](https://github.com/lambduli/monolog).
But back then, I didn't know how to implement the _unification_ in a sensible way.
So, while the _Minilog_ implements unification according to _Martelli and Montanari_,
the first project keeps around sort of a _unification context_ making it very impractical and inefficient.

<details>
  <summary>Show a snippet :computer:</summary>

  ```prolog
  plus(z, N, N).
  plus(s(N), M, s(R)) :- plus(N, M, R).

  times(z, _, z).
  times(s(N), M, A) :- times(N, M, R), plus(R, M, A).

  fact(z, s(z)).
  fact(s(N), R) :- fact(N, PR), times(s(N), PR, R).
  ```
</details>


### [Frea](https://github.com/lambduli/frea) :chestnut:

Small programming language with HM type inference, higher-kinded types, and lazy evaluation.
Implemented as an AST interpreter in Haskell.

It's one of my first _larger_ projects. I wanted to learn about Hindley-Milner type inference and how to implement parametric polymorphism both for functions and data types. Additionally, I learned a bit about laziness.

Originally, the language used to treat recursion on terms very explicitly. There was a `fix` language construct.
Eventually, I replaced the `fix` with an implicit recursion. The type-checker first splits the definitions into groups of mutually recursive definitions and finds a topological ordering on them. This makes it possible to infer the types as polymorphic as possible.

<details>
  <summary>Show a snippet :computer:</summary>
  
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
</details>


### [Lambda-pie](https://github.com/lambduli/lambda-pie)

Three better simple REPLs for `λ->`, `λ2`, and `λΠ`.

<details>
  <summary>Show a snippet :computer:</summary>

  ```
  λ-> >> assume (id :: T -> T) (T :: *) (a :: T) (b :: T)
  λ-> >> id a
        (id a) :: T
  λ-> >> id b
        (id b) :: T
  ```
</details>


### [Lambdas](https://github.com/lambduli/lambdas)

Three simple REPLs for `λ`, `λ->`, and `λ2`.


### Archive

<details>
  <summary>Show the Archive :closed_book:</summary>

  <br/>
  All except the last one were done as a semestral project or a course-work during my master's.
  The last one was just a little thing I did while on a voice call with a friend talking about JavaScript.

  #### [Monolog](https://github.com/lambduli/monolog)

  Small logic programming language inspired by Prolog.
  Implemented as an AST interpreter in Ruby.
  
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
  
  #### [SJS](https://github.com/lambduli/sjs)

  A simple toy compiler from a Lisp-inspired programming language targetting JS.
  Implemented as a parser and a trivial code-gen in Scala.
  
  ```lisp
  (define fact (n)
    (if (or (= n 0) (= n 1))
      1
      (* n (fact (- n 1)))
    )
  )

  (fact 5)
  ```
  
  
  #### [FeenyML](https://github.com/lambduli/FeenyML)
  
  Interpreter and (incomplete) VM for a small programming language inspired by Feeny and ML.
  
  ```ml
  function fact (num) ->
    if num == 0
    then 1
    else num * fact(num - 1);

  fact(5)
  ```
  
  
  #### [DFSM-DSL](https://github.com/lambduli/dfsm-dsl)
  
  JS DSL for implementing Deterministic Finite State Machines using string template literal.

</details>
