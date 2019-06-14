    Title: My experience learning Haskell
    Date: 2016-02-13T19:27:14
    Tags: DRAFT, haskell


tl;dr Haskell will help you in other languages even if you don't use it.

That has been said about [Lisp](http://www.catb.org/~esr/faqs/hacker-howto.html#skills1). Spoiler alert: It's that code is data, and vice versa. However, this property applies even more so to Haskell, since it's very different from mainstream languages. Below the oddly familiar syntax is a completely different model of execution than what we are used to, coming from procedural languages. Most of the unique features of Lisp are now common in dynamically typed programming languages (anonymous functions, garbage collection, introspection, etc.) except for, perhaps, macros. Even macros can be emulated to some degree with hacky usages of Eval. Ruby also has good support for designing DSLs (Domain Specific Languages.) It can be argued that (Python is a form of lisp)[http://norvig.com/python-lisp.html].

After few months in, I found that my style of programming in Python has improved somewhat. I discovered some patterns where functions returning functions greatly reduce duplication. In fact, functions returning functions are one type of the decorator syntax. Also, separating side-effect producing functions from pure functions was a good practice - it lead to less bugs and more testable code. More testable because of the lesser reliance on an external environment.  Now with type hints in Python 3, one can also benefit from defining types and using algebraic data types (using the [NewType](https://docs.python.org/3/library/typing.html#newtype) function.)


I've been fascinated by the Haskell code I've seen, mainly because of its elegance. In 2015, I started learning Haskell seriously. I've been interested in functional languages since college, where I learned scheme and Racket. For some reason, I wasn't thrown off by the parenthesis and the prefix syntax.

I should note, however, that some of the very succinct and elegant examples are not accurate, such as the [Sieve of Eratosthenes](https://www.cs.hmc.edu/~oneill/papers/Sieve-JFP.pdf) one-liner:

```Haskell
primes = sieve [2..]
sieve (p : xs) = p : sieve [x | x <− xs, x ‘mod‘ p > 0]
```

I spent about 3 months learning Haskell, learning completely new concepts and terminology, reading the source code and various documentation. I didn't expect to do anything productive in it. There's a sentiment that it's hard to do useful things in Haskell, mainly because of its strict purity requirements and unusual abstractions.


## How is Haskell different from lisp/racket/clojure?

Haskell belongs to family of functional languages that are statically typed ones with Hinley-Milner type inference.

Besides the ambiguity of calling a language _functional_. (Is Javascript functional?)

A couple of differences from the classic functional languages:

- A superficial difference: Haskell doesn't isn't littered with parenthesis or the _s-expression_ format
- Haskell is strongly and statically typed, with type inference. The Hinley-Milner type system is arguably one of the most advanced type systems in any language. A monad is simpl
- It's purely functional, meaning functions always return the same value, and variables can't change. Some languages related to haskell like SML, OCaml and F# go away with this feature.

A quick glance at wikipedia shows that



## Don't fear the monad

There's a joke that once one understands the monad, you loose the ability to explain it to others.

My view is that it's a typeclass that can be used to chain function calls and pass a __thing__ around. There's also some syntactic sugar around monad chaining.

It's a pretty big deal - One usage allows to have the benefits of non-side-effecting code and also modifying the environment somehow (doing io with the IO monad.)






<!-- more -->
