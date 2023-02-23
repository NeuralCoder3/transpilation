# Neural Transformer Transpilation

The  basic idea of this approach is to generate (parts) of the output using text(-based) transformer networks.
Afterward, the trust (program equivalence) in the output has to be established.


## Advantage
- [ ] Full usage of network to 
    - [ ] synthesize optimal code
    - [ ] connect concepts (unsupervised learning)
- [ ] conceptually simple
- [ ] modular & configurable
- [ ]  

## Difficulties & Limitations
- [ ] no formal guarantees
- [ ] output bound by network capabilities
- [ ] needs to ensure trust afterward
- [ ] can fail unexpectedly
- [ ] needs a LLM

## Details

We start with code in language A and convince a LLM to generate code in language B with the same semantics.
There are many choices of networks to use:
* T5 inspired architectures special trained for programming language tasks
* AST network architectures (need knowledge of language A)
* general purpose LLM
    * zero-shot: Carefully crafted prompt to transpile
    * one-shot/few-shot: give translation examples to guide transpilation (give specifics about the language)
    * finetuning: fine tune the model using a few hundret / thousand examples
* attention based correlation (codex)

Sometimes, LLM run into a wrong direction. Therefore, a restart might be necessary to come up with another (hopefully correct) solution.

The model might produce (depending on the architecture) syntactically and semantically wrong results.

For syntactical issues, we can forward the compiler feedback to iterate until a valid program is returned.

Semantical issues are more difficult to detect and correct.
For the output to be trusted, we need to establish an equivalence with the input.
This can happen in multiple ways:
* correlation based mapping
* automatic equivalence proofs
    * (bounded) translation validation proofs
* property/fuzzing tests

A testing approach is the easiest to implement and maintain for all languages.
Tests can not guarantee correctness. However, a well-tested code is enough in practice. (Note: Depending on the type system and reasoning, whitebox tests could establish correctness)
Additionally, tests provide us with concrete examples of a mis-translation.
We can feed back input-output pairs to refine the result until both programs show the same behaviour.
A tool like quickcheck/hypothesis might help to generate the tests.