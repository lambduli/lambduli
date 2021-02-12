### Hi there 👋

I'am John and I'm interested in PL and Type Systems related stuff.

Some of my favourite work:

### JS DSL for implementating Deterministic Finite State Machines

<!--
  Explain what it's about. Just simple POC for fun.
-->

[repo](https://github.com/Taskkill/dfsm-dsl)

```javascript
  dfsm`
    state default CON${true ? 'NECT' : 'TROLL'}ED
    state OPENED
    state PROCESSED
    state RESETTED

    open CONNECTED -> OPENED .

    add
      OPENED -> OPENED
        ${ (s, newItem) => items.push(newItem) } .

    process
      OPENED -> PROCESSED
        ${ () => items } .

    reset
      PROCESSED -> ${(s, input) => input === 'hard' ? 'RESETTED' : 'OPENED'}
        ${(s, input) => items = input === 'hard' ? [] : items} .
  `
```
___

### Simple programming language with Damas-Hindley-Milner type inference

<!--
Explain what and why.
-->

[repo](https://github.com/Taskkill/frea)

```haskell
  let
    zero = (\ n -> (#= (n, 0)))
  in let rec
    fact n = if (zero n)
              then 1
              else (#* (n, (fact (#- (n, 1)))))
  in (fact 5)
```

___

### Three simple REPLs of various lambda calculi

<!--
Explain what and why.
-->

[repo](https://github.com/Taskkill/lambdas)

```
  [enter λ2 expression]
  :$ (\ a : forall A . A -> A -> A . a) (/ B . (\t : B . (\f : B . t)))
  [command or expression]:$ :type
  :: (forall A . A -> A -> A)
```

___

### REPL for small and simple logic programming language inspired by Prolog

[repo](https://github.com/Taskkill/monolog)

```prolog
  plus(z, N, N).
  plus(s(N), M, s(R)) :- plus(N, M, R).
  times(z, _, z).
  times(s(N), M, A) :- times(N, M, R), plus(R, M, A).
  fact(z, s(z)).
  fact(s(N), R) :- fact(N, PR), times(s(N), PR, R).
```

___

### Very simple compiler from Lisp-inspired programming language compiled to JS

[repo](https://github.com/Taskkill/sjs)

```lisp
  (define fact (n)
    (if (or (= n 0) (= n 1))
      1
      (* n (fact (- n 1)))
    )
  )
```

___

### Interpreter and (incomplete) VM for small programming language inspired by Feeny and ML

[repo](https://github.com/Taskkill/FeenyML)

```ml
  function fact (num) ->
    if num == 0
    then 1
    else num * fact(num - 1);

  fact(10)
```

___

### Core module of the Lambdulus - the λ-calculus evaluator/programming environment

[repo](https://github.com/lambdulus/core) 

<!--
Insert some image of the frontend?
-->

