    Title: My experience learning Haskell
    Date: 2019-05-03T19:27:14
    Tags: haskell, functionalprogramming, DRAFT


tl;dr Haskell will help you in other languages even if you don't use it.

I've always been fascinated by the Haskell code I've seen **[1]**, and I tried [learning Haskell](http://learnyouahaskell.com) briefly in 2010 and when configuring Xmonad. In 2015, I started [learning Haskell seriously](https://en.wikibooks.org/wiki/Write_Yourself_a_Scheme_in_48_Hours) by writing a significant piece of software, a Scheme interpreter, with the help of a tutorial.
After few months in, I found that my style of programming in Python has improved somewhat. I discovered some patterns where functions returning functions greatly reduce duplication. In fact, functions returning functions are one type of the decorator syntax. Also, separating side-effect producing functions from pure functions was a good practice - it lead to less bugs and more testable code. More testable because of the lesser reliance on an external environment.  Now with type hints in Python 3, one can also benefit from defining types and using algebraic data types [NewType](https://docs.python.org/3/library/typing.html#newtype). Python's type hints are nowhere near as mature as Haskell's type system though, and their optional nature in Python changes the experience of using them.

**[1]** I should note that some of the very succinct and elegant examples are not accurate, such as the [Sieve of Eratosthenes](https://www.cs.hmc.edu/~oneill/papers/Sieve-JFP.pdf) two-liner:

```Haskell
primes = sieve [2..]
sieve (p : xs) = p : sieve [x | x <− xs, x `mod` p > 0]
```


## How is Haskell different from lisp/racket/clojure?

Haskell belongs to family of functional languages that are statically typed with [Hindley–Milner type system](https://en.wikipedia.org/wiki/Hindley%E2%80%93Milner_type_system).

Besides the ambiguity of calling a language _functional_. (Is Javascript functional?)

A couple of differences from the classic functional languages:

- A superficial difference: Haskell isn't littered with parenthesis or the _s-expression_ format
- Haskell is strongly and statically typed, with type inference. The Hinley-Milner type system is arguably one of the most advanced type systems in any language. A monad is a typeclass.
- It's purely functional, meaning functions always return the same value, functions can't produce side effects, and variables are immutable. Some languages related to Haskell like SML, OCaml and F# achieve different degrees of these.


## Don't fear the monad

One major feature of Haskell is its monads. There's a joke that once one understands the monad, you loose the ability to explain it to others.

It is based on [relatively simple concepts](http://adit.io/posts/2013-04-17-functors,_applicatives,_and_monads_in_pictures.html).

My view is that it's a typeclass that can be used to chain function calls, and encapsulate other values. There's also some syntactic sugar around monad chaining built into Haskell's syntax, like the [`do`](https://en.wikibooks.org/wiki/Haskell/do_notation) notation and list comprehension.

It's a pretty big deal - it allows most parts of Haskell to remain purely functional while allowing things like IO. It does this by deferring the read/write actions to the runtime. It's more subtle than this, but the idea is that Haskell code that manipulates *instructions to perform IO* can be purely functional.

## Some misconceptions and myths

- **There are no runtime errors**. Runtime errors are still possible. For example, the [error](https://hackage.haskell.org/package/base-4.12.0.0/docs/Prelude.html#v:error) function that can typematch to any function and simply exits.

- **You need to be a genius with a Computer Science PhD to learn/use Haskell**. It's not true. The core language is fairly simple. What's hard about learning Haskell are all the habits and mental model of what a programming language is. Coming from a procedural or C-like language background, a lot of concepts would seem alien or weird. Haskell does come from an academic background, and it shows in a lot of the terminology, but since then it has escaped and seen uses all over the place. For instance, a Haskell music livecoding environment called [TidalCycles](http://tidalcycles.org) is used by artists and musicians who don't know programming, let alone Haskell. Still, it's syntactically correct Haskell code executed in GHCi.


## References


[In-depth: Functional programming in C++](https://gamasutra.com/view/news/169296/Indepth_Functional_programming_in_C.php) by John Carmack
