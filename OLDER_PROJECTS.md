# Older and Smaller Projects :fallen_leaf:

A couple of small lambda evaluators as a reference for my students:

- [A Small λ-evaluator Written in Racket](https://gist.github.com/lambduli/b07c8ce55aa182e3c809f7814eb4feeb) :mushroom:
- [A Small λ-evaluator Written in Elm](https://gist.github.com/lambduli/aa3a1a5ac2716e13cf4351006f0ab559) :mushroom:


All of the following, except the last one, were done as a semestral project or coursework during my master's.
The last one was a little thing I did while talking about JavaScript on a voice call with a friend.

## [Monolog](https://github.com/lambduli/monolog) :maple_leaf:

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

## [SJS](https://github.com/lambduli/sjs) :maple_leaf:

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


<!--
## [FeenyML](https://github.com/lambduli/FeenyML) :maple_leaf:

Interpreter and (incomplete) VM for a small programming language inspired by Feeny and ML.

```ml
function fact (num) ->
  if num == 0
  then 1
  else num * fact(num - 1);

fact(5)
```
-->


## [Call-by-Name ISWIM](https://gist.github.com/lambduli/662c6d934d3e8cd8670670d4468ee906) :mushroom:

Call-by-name operational semantics of ISWIM in PLT REDEX.

```
(((λ unused (λ x (* (+ 1 x) (+ 2 x))))
  ((λ x (x x)) (λ x (x x))))
 (+ 3 4))

:-->>n 72
```


## [Transaction ISWIM](https://gist.github.com/lambduli/1e5f7714fef5269fbd214c587ff29588) :mushroom:

ISWIM with transactional memory in PLT REDEX.

```
(let ([a 80])
  (let ([b 20])
    (let ([adjust ;; Invariant: a + b = 100
           (λ f1
             (λ f2
               (transaction
                 (begin (set a (f1 a))
                        (set b (f2 b))
                        (if0 (+ (+ a b) -100) (λ x x) 1)))))])
      (begin ((adjust (λ a (* a 2))) (λ b (+ b -50))) ;; abort
             ((adjust (λ a (+ a -20))) (λ b (* b 2))) ;; commit
             a))))

evaluates to 60
```


## [$wau ISWIM](https://gist.github.com/lambduli/7ab05d917518b666aa93e9cfee374eb1) :mushroom:

A little experiment with non-strict semantics of ISWIM in PLT REDEX.


## [DFSM-DSL](https://github.com/lambduli/dfsm-dsl) :mushroom:

JS DSL for implementing Deterministic Finite State Machines using string template literal.

```javascript
  const dfsm = require('./dsl').dfsm
  
  
  let factorial = null
  factorial = dfsm`
    state default INIT
    
    call
      INIT -> ${(state, num) => num === 0 ? '1' : `${num}`}
        ${(state, num) => num === 0 ? undefined : factorial.call(num - 1)} .
    
    call
      ${state => state === 'INIT' ? 'NO' : state} -> ${(state, num) => num === 0 ? state : `${Number(state) * num}`}
        ${(state, num) => num === 0 ? state : factorial.call(num - 1)} .
  `
  
  factorial.call(5)
  console.log(factorial.state) // 120
```
