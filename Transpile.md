
- [[Synthesis]]
- [ ] Superoptimizer
- [ ] CEGIS (counterexample guided inductive synthesis) => Gulwani
    - [ ] S. Gulwani, S. Jha, A. Tiwari, and R. Venkatesan. Synthesis of loop-free programs. In Proceedings of the 32nd ACM SIGPLAN Conference on Programming Language Design and Implementation, PLDI ’11, pages 62–73, 2011.
- [ ] depth limited iteration
- [ ] Protobuf universal language
- [ ] 

- [ ] any framework/library in any language
    - [ ] Communication Pipline
        - [ ] C Types
        - [ ] Struct Reification
        - [ ] Interface
        - [ ] String JSonification
- [ ] TransUse
    - [ ] ApiFix
- [ ] Paper Sammlung
- [ ] Interpreter / TransUse instead of Transpile
- [ ] Zip Control Flow => Combine, Split
- [ ] CoPilot Translate
- [ ] ChatGPT Transpile -> DSL

- [ ] incorporate ideas from 22-05 presentation

## Other

- [ ] [Programming Language XKCD](https://imgs.xkcd.com/comics/x.png)
- [ ] Ablaufplan
- [ ] Vortrag
- [ ] Superoptimizer without Speed, high level, control flow
- [ ] incomplete (partial) evaluation 
    - [ ] => on formalized code fragement
- [ ] LSTM AutoComplete
- [ ] Top Down
- [ ] Copy Paste
- [ ] CoPilot Pro/Contra
    - [ ] https://lobste.rs/s/82gnai/is_github_copilot_blessing_curse
    - [ ] https://www.fast.ai/2021/07/19/copilot/
- [ ] Code Difficulty meassure
- [ ] fast-ai
- [ ] Salesforce
- [ ] Anwendungen
    - [ ] DSL Verallgemeinern => Programm Features
- [ ] Tablett
- [ ] GPT Neo
- [ ] Vortrag
- [ ] Interpreter + Partial Eval = Transpiler
- [ ] GPT 3 Proofs
- [ ] [AlphaCode](https://arxiv.org/pdf/2203.07814.pdf)
- [ ] [Proof generation](https://arxiv.org/pdf/2202.01344.pdf)
- [ ] [Proof Generation 2](https://arxiv.org/pdf/2009.03393.pdf)

- [ ] Testing
    - [ ] PropTest (Rust) -> Hypothesis
    - [ ] Hypothesis (Python) -> QuickCheck
    - [ ] QuickCheck (Haskell)
    - [ ] QuickChick (Coq) -> QuickCheck







### TransUse



### Transpile
- Meta Language
    - not necessarily linearizable
    - not necessarily executable
    - Allows easy compilation from every language
    - compiles to other languages (complicated)
    - needs to handle control structures
    - semantical constructs
    - need unifying memory model
    - candidate: lambda calculus + extensions (annotated semantics)
- Control structures
    - Imperativ
        - for
        - while
    - Functional
        - Recursion
        - Tail Recursion
    - Array Programming (Fortran, APL)
        - fold (Tensor)
        - map (Tensor)
    - Higher Order
        - Continuations
        - HO Functions
    - Structures
        - Map
        - Reduce (imperativ)
        - Fold
        - First
        - iter
        - generalized polytypical fold
    - Relations
        - map is fold with id reduction
        - reduce is fold with id mapping
        - while is first
        - for is while
        - for is fold (in most cases)
        - for is iter (conceptually)
        - while is tail recursion
        - fold is higher order function
- Idea: 
    - easy embedding into language
    - rewrite system to normalize (not completely possible only partially) control flow
    - Equality up to Control Flow using SMT (Translation Validation)
    - Transpilation via semantics preserving code synthesis


![[Control_Flow.svg]]

Control als Canvas/Excalidraw/Diagram



### Semantics preserving Code Synthesis