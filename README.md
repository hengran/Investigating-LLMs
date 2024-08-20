# Investigating LLMs

## Three questions:
+ What are the retrieved documents?  ground or misinformation
+ How can LLMs utilize the retrieved documents?  prompt tuning
+ How do LLMs generate answers based on the retrieved documents? decoding

## Problem in LLMs

+ Trustworthiness:  reliability, safety, fairness, resistance to misuse, explainability and reasoning, adherence to social norms, and robustness. [[Trustworthy LLMs: a Survey and Guideline for Evaluating Large Language Models' Alignment](https://arxiv.org/abs/2308.05374)]
+ Factual Consistency. [[Evaluating the Factual Consistency of Large Language Models Through News Summarization](https://aclanthology.org/2023.findings-acl.322.pdf)]
+ Hallucination [[Siren’s Song in the AI Ocean: A Survey on Hallucination in Large Language Models](https://arxiv.org/abs/2309.01219)]:
  - Input-conflicting hallucination, where LLMs generate content that deviates from the source input provided by users.
  - Context-conflicting hallucination, where LLMs generate content that conflicts with previously generated information by itself.
  - Fact-conflicting hallucination, where LLMs generate content that is not faithful to established world knowledge.
    
## Problem in retrieval-augmented LLMs
+ Retrieval process:
  - misinformation [[Discern and Answer: Mitigating the Impact of Misinformation in Retrieval-Augmented Models with Discriminators](https://browse.arxiv.org/pdf/2305.01579.pdf)] 
+ LLMs performance:
  -  Noise Robustness, negative rejection, information integration, and dealing with false information [[When Not to Trust Language Models: Investigating Effectiveness of Parametric and Non-Parametric Memories](https://aclanthology.org/2023.acl-long.546.pdf)]
  -  Faithfulness[[Evaluating Correctness and Faithfulness of Instruction-Following Models for Question Answering](https://arxiv.org/abs/2307.16877)]: It is a kind of Input-conflicting hallucination. [[Siren’s Song in the AI Ocean: A Survey on Hallucination in Large Language Models](https://arxiv.org/abs/2309.01219)]
  -  Knowledge conflicts. [[Adaptive Chameleon or Stubborn Sloth: REVEALING THE BEHAVIOR OF LARGE LANGUAGE MODELS IN KNOWLEDGE CONFLICTS](https://browse.arxiv.org/pdf/2305.13300.pdf)] [[Trusting Your Evidence: Hallucinate Less with Context-aware Decoding](https://arxiv.org/abs/2305.14739)]
  -  Factual Knowledge Boundary.  [[Investigating the Factual Knowledge Boundary of Large Language Models with Retrieval Augmentation](https://arxiv.org/abs/2307.11019)]
  -  Combine non-parametric and parametric memories. [[When Not to Trust Language Models: Investigating Effectiveness of Parametric and Non-Parametric Memories](https://aclanthology.org/2023.acl-long.546.pdf)]

## Investigating LLMs with summarization

+ **Derek Tam et al: Evaluating the Factual Consistency of Large Language Models Through News Summarization** [[paper](https://aclanthology.org/2023.findings-acl.322.pdf)] 2023, ACL findings
  
   - **key point:** This paper evaluates 23 large language models ranging from 1B to 176B parameters from six different model families including BLOOM and OPT, and they found that existing LLMs generally assign a higher score to factually consistent summaries than to factually inconsistent summaries. 
+ **Weijia Shiet al: Trusting Your Evidence: Hallucinate Less with Context-aware Decoding** [[paper](https://arxiv.org/abs/2305.14739)] 2023.05
  - **Key point:** This paper presents context-aware decoding (CAD), which follows a contrastive output distribution that amplifies the difference between the output probabilities when a model is used with and without context. Without additional training, CAD significantly improves the faithfulness of different LM families, including OPT, GPT, LLaMA and FLAN-T5 for summarization tasks.


## Survey on LLMs

+ **Yang Liu et al: Trustworthy LLMs: a Survey and Guideline for Evaluating Large Language Models' Alignment** [[paper](https://arxiv.org/abs/2308.05374)] 2023.08
  + **Key point:** This paper presents a comprehensive survey of key dimensions that are crucial to consider when assessing LLM trustworthiness. The survey covers seven major categories of LLM trustworthiness: reliability, safety, fairness, resistance to misuse, explainability and reasoning, adherence to social norms, and robustness. Each major category is further divided into several sub-categories, resulting in a total of 29 sub-categories.
+ **Yue Zhang et al:Siren’s Song in the AI Ocean: A Survey on Hallucination in Large Language Models** [[paper](https://arxiv.org/abs/2309.01219)] 2023.09
  + **Key point:** An overview of the problem of large-model hallucinations is presented in terms of detection, explanation and mitigation.
+ **Ziwei Ji et al: Survey of hallucination in natural language generation**[paper](https://dl.acm.org/doi/abs/10.1145/3571730) 2023
+ **Bingbing Wen et al: Know Your Limits: A Survey of Abstention in Large Language Models** [paper](https://www.llwang.net/assets/pdf/2024_wen_abstention-survey_arxiv.pdf)
  + **Key point:** Abstention, the refusal of large language models (LLMs) to provide an answer, is increasingly recognized for its potential to mitigate hallucinations and enhance safety in LLM systems. In this survey, we introduce a framework to examine abstention from three perspectives: the query, the model, and human values. 




## Investigating LLMs with retrieval-augmented 
+ **Vaibhav Adlakha et al: Evaluating Correctness and Faithfulness of Instruction-Following Models for Question Answering**  [[paper](https://arxiv.org/abs/2307.16877)] 2023.07
  - **Key point:** This paper investigates the performance of instruction-following models across three information-seeking QA tasks. This paper uses both automatic and human evaluation to evaluate these models along two dimensions: 1) how well they satisfy the user's information need (correctness), and 2) whether they produce a response based on the provided knowledge (faithfulness)(Tips: provied knowledge is ground_truth passages, NQ and HotpotQA have ground_truth passages).
    
+ **Ruiyang Ren et.al: Investigating the Factual Knowledge Boundary of Large Language Models
with Retrieval Augmentation** [[paper](https://arxiv.org/abs/2307.11019)] 2023.07
  - **Key point:** This paper presents an initial analysis of the factual knowledge boundaries of LLMs and how retrieval augmentation affects LLMs on open-domain QA.
    
+ **Jian Xie et al:Adaptive Chameleon or Stubborn Sloth: REVEALING THE BEHAVIOR OF LARGE LANGUAGE MODELS IN KNOWLEDGE CONFLICTS**  [[paper](https://browse.arxiv.org/pdf/2305.13300.pdf)] 2023.10
  + **Key point:** This paper presents the first comprehensive and controlled investigation into the behavior of LLMs when encountering knowledge conflicts.
    
+ **Giwon Hong et al: Discern and Answer: Mitigating the Impact of Misinformation in Retrieval-Augmented Models with Discriminators**  [[paper](https://browse.arxiv.org/pdf/2305.01579.pdf)] 2023.05
  + **Key point:** This paper studies a more realistic scenario in which retrieved documents may contain misinformation, causing conflicts among them. We observe that the existing models are highly brittle to such information in both fine-tuning and in-context few-shot learning settings. This paper finds that explicitly fine-tuning a discriminator or prompting to elicit discrimination capability in GPT-3 significantly improve LMs' robustness to knowledge conflicts
    
+ **Jiawei Chen et al: Benchmarking Large Language Models in Retrieval-Augmented Generation** [[paper](https://arxiv.org/abs/2309.01431)] 2023.09
  + **Key point:** This paper establishes Retrieval-Augmented Generation Benchmark (RGB) and evaluates 6 representative LLMs in terms of Noise Robustness, negative rejection, information integration, and dealing with false information.
    
+ **Alex Mallen et al: When Not to Trust Language Models: Investigating Effectiveness of Parametric and Non-Parametric Memories** [[paper](https://aclanthology.org/2023.acl-long.546.pdf)] 2023, ACL long
  + **Key point:** This paper aims to understand LMs' strengths and limitations in memorizing factual knowledge, by conducting large-scale knowledge probing experiments of 10 models and 4 augmentation methods on PopQA, our new open-domain QA dataset with 14k questions. This paper finds that LMs struggle with less popular factual knowledge, and that scaling fails to appreciably improve memorization of factual knowledge in the long tail.
    
+ **Siqing Huo et al: Retrieving Supporting Evidence for Generative Question**  [[paper](https://arxiv.org/pdf/2309.11392.pdf)] 2023.09
  + **Key point:** This paper reports two simple experiments to automatically validate generated answers against a corpus.
    
+ **Hengran Zhang et al: Iterative Utility Judgment Framework via LLMs Inspired by Relevance in Philosophy** [[paper](https://dl.acm.org/doi/pdf/10.1145/3626772.3657784)] 2024.03
   + **Key point:** This paper analyze LLMs in utility judgmens in retrieval-augmented generation.
  


 


