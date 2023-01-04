# Transpilation

In this repository, we investigate different aspects and solution (ideas) to the problem of having too many programming languages.

![[logo.png]]

## Problem

```
TLDR: There are features bound to programming languages that are conceptually independent of the concrete language used.

With over 9000 programming languages in use, porting these tools by hand to all popular languages is infeasible.

In conclusion, this leads to unncessesary work and unavailability of tools.
```


There are a lot (current estimate >9000) of programming languages (at least 1000 with some hundret of active use and possible many more -- there are at least 3570 registered esoteric programming languages).

Not every language is the same.
We will focus on general-use programming languages (either by design or by use) and ignore special use programming languages.
For these languages we can find multiple similiarities and diference.

There are many aspects to languages (non-exclusive) (I only give one or two examples per class -- many languages are omitted):
* dependent type systems (Gallina, Idris)
* functional programming (Haskell, OCaml)
* imperative (C++)
* object oriented (Kava)
* dynamically typed (python, javascript)
* array programming (APL, Fortran)
* low-level (C, Rust)
* Lisp
* prototype (Lua)
* scripting (python, lua)
* concurrent (Rust)
* logical (prolog)
* ....
And many more paradigms can be found on [Wikipedia](https://en.wikipedia.org/wiki/Programming_paradigm).


There are good (my opinion) reasons to use different languages:
* features suited for a special use case
    * low level memory control
    * fully manages memory 
* incompatible features that you like
    * imperative scripting
    * dependent type systems
    * pure functional programming
    * simplicity (depedent on special cases -> maybe consider staging)
    * complexity (depedent on special cases -> maybe consider staging)
* design around special use case (not just primitives)

There are also not so good (my opinion) reasons:
* Tools available for this language
    * Analyzers
    * IDEs
    * Libraries
    * Frameworks
    * Standard library functions
* Compiler
    * Speed
    * Optimizations
* Userbase
* Language Primitives

I am not saying, it is wrong to choose a language by any of the second set of points.
However, I propose that these point do not have to / should not influence the choice of language.
On a more abstract level, these points can (for the most part) be isolated from the language itself.
They are only linked by implementation to a language but not conceptually as they apply to programming itself.
In the end, a programming language is only a tool to express semantics of a procedure manipulating data. How we express this can differ in syntax but is conceptually the same.

Even though the syntax might look quite different between languages,
an experienced programmer can pick up any language fast with only a few examples.
They will tell you that the underlying principles between most languages are the same.
A for loop in C is the same as in Java or Python. 
The `map` function of Haskell, the `.map` in Java, the for loop in C, and the list comprehension in Python all look different but express the same semantics.
A while loop and a tail recursive function are quite different in appearance, but every undergrad student learns that they function the same and result in very similar assembly code. 

Despite these similarities or due to the freedom of expression, many languages developed and are in use.
It is good that you can freely choose how you want to write code.
However, it is a shame when tools are locked to a language or need time-intensive ports and re-implementations.

### Examples

Only to name a few examples, we can look at common libraries:

[**Tensorflow**](https://www.tensorflow.org/) and [**PyTorch**](https://pytorch.org/) are widely used and very successful machine-learning tools.
There exist many (one for every popular language) implementations of the frameworks that effectively call the underlying C libraries. Some languages have more sophisticated libraries that embed the frameworks as DSL / reify parts of the language into the frameworks.
Additionally, some languages have libraries building up on the basic frameworks.
Python has one of the best supports for these frameworks.

It is tedious and schematic to write all the boilerplate to call the libraries.
Some language pairs have semi-automation to generate ABI/FFI. 
But these tools only help for special cases and do not solve the problem in general.
The additional problem of advanced interfaces and libraries are currently not solved.

One could even argue, that for many applications the framework itself could be an implementation-detail: The programmer wants to express a ML-model. The details could be hidden by a common interface. There are libraries available that do this. However, it is imaginable that such an interface could be infered automatically and translate between both libraries without human interaction.

The [**QuickCheck**](https://en.wikipedia.org/wiki/QuickCheck) framework is a popular combinator library that helps in generating test cases.
It originates in Haskell and was sucessfully applied to other languages as well.
There is QuickChick in Coq, Hypothesis in Python, based on Hypothesis there is PropTest in Rust, and there are 60 more **re**-implementations in other languages.
To be more precise, there are at least six quickcheck re-implementations for python on Github with at least 15 stars.
Some of these re-implementation "only" support random test generation while others are more fully features including features like test minimization.

Before quickchick was re-implemented, the default way was to write the code, expose a FFI and use quickchick externally by hand.

Another common example are **SQL** frameworks that are re-implemented in every language. More sophisticated features like syntax checking, dummy data generation, compile time checking, ... are left on the way and are only available in very few languages.


To give a last example, [**SOSML**](https://sosml.org/) is an online interpreter for Standard ML with a nice interface.
The SML implementation is written from scratch by students.
However, Saarland University switched from SML to OCaml.
Theoretically, the difference between SML and OCaml are just some renamings.

But the correct handling of these changes either require a transpiler between OCaml and SML (including a parser for OCaml) or changes in the SML interpreter (required in-depth knowledge of the code). See [SOOCaml](https://github.com/NeuralCoder3/SOOCaml-frontend) for a discussion.

This is tedious and could theoretically be automated.
However, until somebody takes time to deeply understand the interpreter, the current solution is to abandon SOSML or to patch in a third-party OCaml interpreter (transpiled to Javascript).



## Goal


## Ideas


Verifying Compiler => keep semantics, preserve properties

### TransPile

### TransUse

ABI/FFI -> DSL Github
APIFix