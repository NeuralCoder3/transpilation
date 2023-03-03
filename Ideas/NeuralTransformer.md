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


## Experiments & Results

[see subfolder]


## Related Literature
Some literature that applies specifically to this experiment.
This includes prompt engeneering attempt especially for \*GPT\* models.
- GPT3 conditioning
    - https://news.ycombinator.com/item?id=34869960#34873669
- ChatGPT conditioning
    - [Overview](https://www.jailbreakchat.com/)
    - [prompt collection](https://github.com/f/awesome-chatgpt-prompts)
    - [Dan 5.0](https://www.reddit.com/r/ChatGPT/comments/10tevu1/new_jailbreak_proudly_unveiling_the_tried_and/)
        - [Dan 6.0](https://www.reddit.com/r/ChatGPT/comments/10vinun/presenting_dan_60/)
        - [SDAN](https://www.reddit.com/r/ChatGPT/comments/10vlzbo/presenting_sdan_simple_dan/)
    - [SQL analyst in 26 recursive prompts](https://www.patterns.app/blog/2023/01/18/crunchbot-sql-analyst-gpt/)
        - [Hackernews](https://news.ycombinator.com/item?id=34521149)
    - [Midjouney Prompt Engine 3](https://www.reddit.com/r/midjourney/comments/11chf6s/version_3_of_my_chatgpt_prompting_machine_it_now/)
    - [stable diffusion prompter](https://www.reddit.com/r/StableDiffusion/comments/11cfe1i/is_there_a_chatgpt_prompt_to_create_sd_prompts/)
- LLM Prompt Engeneering
    - [Microsoft Prompt Engine](https://news.ycombinator.com/item?id=34811070) 
- [ChatGPT official API](https://openai.com/blog/introducing-chatgpt-and-whisper-apis)
- [Pinecone long term vector memory](https://www.pinecone.io/)
- [Chat from GPT](https://github.com/Kav-K/GPT3Discord) [Author Response](https://old.reddit.com/r/GPT3/comments/zxs18b/gpt3dalle2_discord_bot_with_mediumlong_term_memory/j22a0vk/) 

<details>
<summary>Table prompt GUI Interaction</summary>
INSTRUCTIONS: Provide a {text) that you would like to make changes to. Generate a TABLE with 2
columns, one with numbers and one with 5 different writing styles. After the TABLE is generated, ask
the question "What writing style would you like to implement? Pick one from the table above" below
the TABLE. Wait for the user to pick a number.


text = 

Execute the INSTRUCTIONS in a TABLE format:
</details>