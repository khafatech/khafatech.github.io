    Title: My experience learning Haskell
    Date: 2016-02-13T19:27:14
    Tags: haskell, programming languages


tl;dr Haskell will help you in other languages even if you don't use it.

That has been said about Lisp [put reference], but I think this applies even more so to Haskell, since it's so different than mainstream languages. Below the oddly familiar syntax is a completely different model of execution than what we are used to, coming from procedural languages. Most of the unique features of Lisp are now common in dynamic programming languages (anonymous functions, garbage collection, introspection, etc.) Except perhaps, macros. Though that can be emulated to some degree with hackish usages of Eval, and Ruby also has good support for designing DSLs (Domain Specific Languages.)cheme. It can be argued that Python is a form of lisp [link to norvig's].

After few months in, I found that my style of programming in Python has improved somewhat. I discovered some patterns where functions returning functions greatly reduce duplication. Also, separating side-effect producing functions from pure functions was a good practice - it lead to less bugs and more testable code. More testable because of the lesser reliance on an external environment.  Now with type hints in Python 3, one can also benefit from defining types and using algebriac data types (using the [NewType](https://docs.python.org/3/library/typing.html#newtype) function.)



I've been fascinated by the Haskell code I've seen, mainly because of its elegance. In 2015, I started learning Haskell seriously. I've been interested in functional languages since college, where I learned scheme and Racket. For some reason, I wasn't thrown off by the parenthisis, and that "nobody gets a job writing scheme."

I should note, however, that some of the very succint and elegant examples are actually wrong. [put Seive link]

I spent about 3 months learning Haskell, learning completely new concepts and terminology, reading the source code and various documentation. I didn't expect to do anything productive in it. It's well-known that it's "hard" to do useful things in haskell, mainly because of its strict purity requirements.



## How is haskell different from lisp/racket/clojure?

Haskell, on the other hand, bel family of functional languages - statically typed ones with Hinley-Milner type inference.

Besides the ambiguity of calling a language _functional_. (Is Javascript functional?)


A couple of differences from the classic functional languages:

- A superficial difference: Haskell doesn't isn't littered with parenthesis or the _s-expression_ format
- Haskell is strongly and statically typed, with type inference. The hindly milner type system is arguably one of the most advanced type systems in any language. A monad is simpl
- It's purely functional, meaning functions always return the same value, and variables can't change. Some languages related to haskell like SML, OCaml and F# go away with this feature.

A quick glance at wikipedia shows that



## Don't fear the monad

There's a joke that once one understands the monad, you loose the ability to explain it to others.

My view is that it's a typeclass that can be used to chain function calls and pass a __thing__ around. There's also some syntactic sugar around monad chaining.

It's a pretty big deal - One usage allows to have the benefits of non-side-effecting code and also modifying the environment somehow (doing io with the IO monad.)






<!-- more -->
