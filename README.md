# ASQP-Survey

Resources for our survey paper **A Survey on Aspect Sentiment Quadruple Prediction: Modeling Paradigms, Evaluations, and Challenges**.

The survey groups methods for aspect sentiment quadruple prediction (ASQP), also called aspect-category-opinion-sentiment (ACOS) quadruple extraction, by the mechanism that produces the final quadruples. This repository lists every surveyed method under its paradigm, with links to the paper and the code, and every dataset discussed in the survey, with a link to the data when it is public.

> The paper link will be added here after publication. If we missed a paper or a dataset, please open an issue or a pull request.

## Contents

- [Task](#task)
- [Taxonomy](#taxonomy)
- [Paper list](#paper-list)
  - [Token-Level Classification (TokenClass)](#token-level-classification-tokenclass)
  - [Machine Reading Comprehension (MRC)](#machine-reading-comprehension-mrc)
  - [Sequence-to-Sequence Generation (Seq2Seq)](#sequence-to-sequence-generation-seq2seq)
  - [Sequence-to-Tree Prediction (Seq2Tree)](#sequence-to-tree-prediction-seq2tree)
  - [Pipeline](#pipeline)
- [Datasets](#datasets)
  - [Open datasets](#open-datasets)
  - [Non-open datasets](#non-open-datasets)
- [Citation](#citation)

## Task

Given a review, ASQP predicts every quadruple (aspect category, aspect term, opinion term, sentiment polarity). An aspect or an opinion can be implicit, and it is then written as `NULL`.

| Review | Quadruples |
|---|---|
| The pasta was great, but the waiter was rude. | (FOOD#QUALITY, pasta, great, positive), (SERVICE#GENERAL, waiter, rude, negative) |
| Never going back. | (RESTAURANT#GENERAL, NULL, NULL, negative) |

## Taxonomy

Each method belongs to exactly one paradigm. A method is a **pipeline** when its stages are trained or prompted separately and a later stage takes a discrete prediction of an earlier stage as input. Every other method is **single-stage**, and it takes the paradigm of the mechanism that produces its final quadruples. Pipelines are split by their final stage, and Seq2Tree methods by the way they build the tree.

```
ASQP
├── Single-stage
│   ├── Token-Level Classification (TokenClass)
│   ├── Machine Reading Comprehension (MRC)
│   ├── Sequence-to-Sequence Generation (Seq2Seq)
│   └── Sequence-to-Tree Prediction (Seq2Tree)
│       ├── Constrained tree generation
│       ├── Chart parsing
│       └── Tree-slot classification
└── Pipeline
    ├── Discriminative final stage
    └── Generative final stage
```

In total, the list holds 124 methods. Within each paradigm, papers are ordered from the oldest to the newest.

## Paper list

### Token-Level Classification (TokenClass)

Every token or token pair gets one label from a fixed set, and rules decode the quadruples from the label grid.

| Year | Title | Venue | Paper | Code |
|---|---|---|---|---|
| 2023 | A Fine-grained Sentiment Analysis Method Based On A Unified Framework | ISCTech | [Paper](https://doi.org/10.1109/ISCTech60480.2023.00012) | - |
| 2023 | A Model Ensemble Approach for Conversational Quadruple Extraction | NLPCC | [Paper](https://doi.org/10.1007/978-3-031-44699-3_16) | - |
| 2023 | A Unified One-Step Solution for Aspect Sentiment Quad Prediction | Findings of ACL | [Paper](https://doi.org/10.18653/v1/2023.findings-acl.777) | [Code](https://github.com/Datastory-CN/ASQP-Datasets) |
| 2023 | An Aspect-Category-Opinion-Sentiment Quadruple Extraction with Distance Information for Implicit Sentiment Analysis | ITC | [Paper](https://doi.org/10.5755/j01.itc.52.2.32903) | - |
| 2023 | Aspect sentiment quadruple extraction based on the sentence-guided grid tagging scheme | WWW | [Paper](https://doi.org/10.1007/s11280-023-01185-9) | - |
| 2023 | Conversational Aspect-Based Sentiment Quadruple Analysis with Consecutive Multi-view Interaction | NLPCC | [Search](https://scholar.google.com/scholar?q=Conversational+Aspect-Based+Sentiment+Quadruple+Analysis+with+Consecutive+Multi-view+Interaction) | - |
| 2023 | DiaASQ: A Benchmark of Conversational Aspect-based Sentiment Quadruple Analysis | Findings of ACL | [Paper](https://doi.org/10.18653/v1/2023.findings-acl.849) | [Code](https://github.com/unikcc/DiaASQ) |
| 2023 | Enhancing Conversational Aspect-Based Sentiment Quadruple Analysis with Context Fusion Encoding Method | NLPCC | [Search](https://scholar.google.com/scholar?q=Enhancing+Conversational+Aspect-Based+Sentiment+Quadruple+Analysis+with+Context+Fusion+Encoding+Method) | - |
| 2023 | Improving Conversational Aspect-Based Sentiment Quadruple Analysis with Overall Modeling | NLPCC | [Paper](https://doi.org/10.1007/978-3-031-44699-3_14) | [Code](https://github.com/terence1023/NLPCC2023-DiaASQ) |
| 2023 | Syntax-Based Aspect Sentiment Quad Prediction by Dual Modules Neural Network for Chinese Comments | CMC | [Paper](https://doi.org/10.32604/cmc.2023.037060) | - |
| 2024 | DMIN: A Discourse-specific Multi-granularity Integration Network for Conversational Aspect-based Sentiment Quadruple Analysis | Findings of ACL | [Paper](https://doi.org/10.18653/v1/2024.findings-acl.966) | [Code](https://github.com/SIGSDSscau/DMIN) |
| 2024 | Dynamic Multi-Scale Context Aggregation for Conversational Aspect-Based Sentiment Quadruple Analysis | ICASSP | [Paper](https://doi.org/10.1109/ICASSP48485.2024.10447873) | [Code](https://github.com/qdCassie-Li/DMCA) |
| 2024 | Harnessing Holistic Discourse Features and Triadic Interaction for Sentiment Quadruple Extraction in Dialogues | AAAI | [Paper](https://doi.org/10.1609/aaai.v38i16.29807) | [Code](https://github.com/WHULACC/H2DT) |
| 2024 | iACOS: Advancing Implicit Sentiment Extraction with Informative and Adaptive Negative Examples | NAACL | [Paper](https://doi.org/10.18653/v1/2024.naacl-long.241) | [Code](https://github.com/jiadongzh/iacos) |
| 2024 | Label-semantics enhanced multi-layer heterogeneous graph convolutional network for Aspect Sentiment Quadruplet Extraction | ESWA | [Paper](https://doi.org/10.1016/j.eswa.2024.124523) | [Code](https://github.com/Thirring/LSEMH-GCN) |
| 2024 | Opinion-Tree-guided Contrastive Learning for Aspect Sentiment Quadruple Prediction | CSCWD | [Paper](https://doi.org/10.1109/CSCWD61410.2024.10580240) | - |
| 2024 | Span-Pair Interaction and Tagging for Dialogue-Level Aspect-Based Sentiment Quadruple Analysis | WWW | [Paper](https://doi.org/10.1145/3589334.3645355) | [Code](https://github.com/zhoucz97/MRM4DiaASQ) |
| 2024 | Triple GNNs: Introducing Syntactic and Semantic Information for Conversational Aspect-Based Quadruple Sentiment Analysis | CSCWD | [Paper](https://doi.org/10.1109/CSCWD61410.2024.10580730) | [Code](https://github.com/nlperi2b/Triple-GNNs-) |
| 2025 | An Attention Mask Mechanism for Conversational Aspect-based Sentiment Quadruple Analysis | ICCNSE | [Paper](https://doi.org/10.1109/ICCNSE66404.2025.11144058) | - |
| 2025 | CACA: Context-Aware Cross-Attention Network for Extractive Aspect Sentiment Quad Prediction | ICCL | [Search](https://scholar.google.com/scholar?q=CACA%3A+Context-Aware+Cross-Attention+Network+for+Extractive+Aspect+Sentiment+Quad+Prediction) | [Code](https://github.com/DMIRLAB-Group/CACA) |
| 2025 | Context-Aware Directed Acyclic Graph Network for Conversational Aspect-Based Sentiment Quadruple Analysis | IEEE Access | [Paper](https://doi.org/10.1109/ACCESS.2025.3605729) | - |
| 2025 | Dialogue Multi-dimensional Feature Dividing and Fusion Model for Dialogue Aspect-Based Sentiment Quadruple Analysis | NLPCC | [Search](https://scholar.google.com/scholar?q=Dialogue+Multi-dimensional+Feature+Dividing+and+Fusion+Model+for+Dialogue+Aspect-Based+Sentiment+Quadruple+Analysis) | - |
| 2025 | Harnessing Syntax GCN and Multi-View Interaction for Conversational Aspect-Based Quadruple Sentiment Analysis | IEEE Access | [Paper](https://doi.org/10.1109/ACCESS.2025.3562967) | - |
| 2025 | IFusionQuad: A novel framework for improved aspect-based sentiment quadruple analysis in dialogue contexts with advanced feature integration and contextual CloBlock | ESWA | [Paper](https://doi.org/10.1016/j.eswa.2024.125556) | [Code](https://github.com/Joeisjoejoe/IFusionQuad) |
| 2025 | Inter-sentence Context Modeling and Structure-aware Representation Enhancement for Conversational Sentiment Quadruple Extraction | EMNLP | [Paper](https://doi.org/10.18653/v1/2025.emnlp-main.867) | - |
| 2025 | LnHGN: Label and Neighborhood-Aware Heterogeneous Graph Network for Conversational Aspect Sentiment Quadruple Analysis | AIHCIR | [Paper](https://doi.org/10.1109/AIHCIR67580.2025.11405423) | - |
| 2025 | MADIAT: enhancing conversational aspect-based sentiment quadruple analysis with multi-view adaptive dynamic interaction and adversarial training | IJMLC | [Paper](https://doi.org/10.1007/s13042-025-02736-4) | - |
| 2025 | Memory: an Adaptive Contextual Memory Framework for Aspect-Based Dialogue Sentiment Quadruple Analysis | ICCCBDA | [Paper](https://doi.org/10.1109/ICCCBDA64898.2025.11030441) | - |
| 2025 | Modeling hierarchical structure for conversational aspect-based quadruple sentiment analysis | Neurocomputing | [Paper](https://doi.org/10.1016/j.neucom.2025.131055) | - |
| 2025 | Multi-dimensional feature interaction for Conversational Aspect-Based Quadruple Sentiment Analysis | NPL | [Paper](https://doi.org/10.1007/s11063-025-11721-5) | - |
| 2025 | Multi-level Association Refinement Network for Dialogue Aspect-based Sentiment Quadruple Analysis | ACL | [Paper](https://doi.org/10.18653/v1/2025.acl-long.686) | - |
| 2025 | PMN: A prototype network based metric framework for solving aspect-based sentiment analysis tasks | Neurocomputing | [Paper](https://doi.org/10.1016/j.neucom.2025.131155) | - |
| 2025 | SARA: Span-aware framework with relation-augmented grid tagging for conversational aspect-based sentiment quadruple analysis | EAAI | [Paper](https://doi.org/10.1016/j.engappai.2025.110915) | - |
| 2025 | SGCD: Subtask-Guided Causal-Debiasing Framework for Robust Cross-Utterance Sentiment Quadruple Extraction in Dialogues | Findings of EMNLP | [Paper](https://doi.org/10.18653/v1/2025.findings-emnlp.613) | [Code](https://github.com/hustselab511/SGCD) |
| 2025 | TTRCD: Task-Specific Token-Level Representations and Cross-Utterance Dependencies for Conversational Aspect-Based Sentiment Quadruple Analysis | ICONIP | [Search](https://scholar.google.com/scholar?q=TTRCD%3A+Task-Specific+Token-Level+Representations+and+Cross-Utterance+Dependencies+for+Conversational+Aspect-Based+Sentiment+Quadruple+Analysis) | - |
| 2025 | Unified Grid Tagging Scheme for Aspect Sentiment Quad Prediction | COLING | [Search](https://scholar.google.com/scholar?q=Unified+Grid+Tagging+Scheme+for+Aspect+Sentiment+Quad+Prediction) | - |
| 2026 | Context Relation-Aware and Fine-Grained Token Interaction for Dialogue-Level Aspect-Based Sentiment Quadruple Analysis | ICMR | [Paper](https://doi.org/10.1145/3805622.3810621) | - |
| 2026 | Discovering consumer sentiment in E-commerce conversations: A dialogue graph attention network approach | ECRA | [Paper](https://doi.org/10.1016/j.elerap.2026.101606) | [Code](https://github.com/Yuki-takuya-kun/DiaGAT) |
| 2026 | SEAD-MGFE-Net: Schrödinger equation-based adaptive dropout multi-granular feature enhancement network for conversational aspect-based sentiment quadruple analysis | IS | [Paper](https://doi.org/10.1016/j.ins.2025.122684) | [Code](https://github.com/HatsuneMikuLW/SEAD-MGFE-Net) |
| 2026 | SHARP: Structure-aware heterogeneous attention with rotational processing for conversational sentiment quadruple analysis | ESWA | [Paper](https://doi.org/10.1016/j.eswa.2026.132835) | [Code](https://atomgit.com/aibd/SHARP) |

### Machine Reading Comprehension (MRC)

Each element is requested by a natural-language query, and later queries contain the answers of earlier ones.

| Year | Title | Venue | Paper | Code |
|---|---|---|---|---|
| 2023 | Enhanced Machine Reading Comprehension Method for Aspect Sentiment Quadruplet Extraction | ECAI | [Paper](https://doi.org/10.3233/FAIA230600) | [Code](https://github.com/Little-Yeah/EMCR) |
| 2024 | Query-induced multi-task decomposition and enhanced learning for aspect-based sentiment quadruple prediction | EAAI | [Paper](https://doi.org/10.1016/j.engappai.2024.108609) | [Code](https://github.com/codewen77/MRC-CLRI) |

### Sequence-to-Sequence Generation (Seq2Seq)

The whole quadruple set is generated as one flat text sequence and parsed back into quadruples. Fine-tuned and prompted LLMs belong here.

| Year | Title | Venue | Paper | Code |
|---|---|---|---|---|
| 2021 | Aspect Sentiment Quad Prediction as Paraphrase Generation | EMNLP | [Paper](https://doi.org/10.18653/v1/2021.emnlp-main.726) | [Code](https://github.com/IsakZhang/ABSA-QUAD) |
| 2022 | Aspect-Category-Opinion-Sentiment Extraction Using Generative Transformer Model | RIVF | [Paper](https://doi.org/10.1109/RIVF55975.2022.10013820) | - |
| 2022 | Generative Aspect-Based Sentiment Analysis with Contrastive Learning and Expressive Structure | Findings of EMNLP | [Paper](https://doi.org/10.18653/v1/2022.findings-emnlp.451) | [Code](https://github.com/jpeper/GEN_SCL_NAT) |
| 2022 | Improving Aspect Sentiment Quad Prediction via Template-Order Data Augmentation | EMNLP | [Paper](https://doi.org/10.18653/v1/2022.emnlp-main.538) | [Code](https://github.com/hmt2014/AspectQuad) |
| 2023 | AQE: Argument Quadruplet Extraction via a Quad-Tagging Augmented Generative Approach | Findings of ACL | [Paper](https://doi.org/10.18653/v1/2023.findings-acl.59) | [Code](https://github.com/guojiapub/QuadTAG) |
| 2023 | BART-based contrastive and retrospective network for aspect-category-opinion-sentiment quadruple extraction | IJMLC | [Paper](https://doi.org/10.1007/s13042-023-01831-8) | [Code](https://github.com/xiaodou12046/BART_CRN) |
| 2023 | Boosting Aspect Sentiment Quad Prediction by Data Augmentation and Self-Training | IJCNN | [Paper](https://doi.org/10.1109/IJCNN54540.2023.10191634) | - |
| 2023 | Easy-to-Hard Learning for Information Extraction | Findings of ACL | [Paper](https://doi.org/10.18653/v1/2023.findings-acl.754) | [Code](https://github.com/DAMO-NLP-SG/IE-E2H) |
| 2023 | From Implicit to Explicit: A Simple Generative Method for Aspect-Category-Opinion-Sentiment Quadruple Extraction | IJCNN | [Paper](https://doi.org/10.1109/IJCNN54540.2023.10191098) | - |
| 2023 | Generative Data Augmentation for Aspect Sentiment Quad Prediction | SEM | [Paper](https://doi.org/10.18653/v1/2023.starsem-1.12) | [Code](https://github.com/AnWang-AI/AugABSA) |
| 2023 | Implicit Sentiment Extraction Using Structure Generation with Sentiment Instructor Prompt Template | ADMA | [Search](https://scholar.google.com/scholar?q=Implicit+Sentiment+Extraction+Using+Structure+Generation+with+Sentiment+Instructor+Prompt+Template) | - |
| 2023 | Indo LEGO-ABSA: A Multitask Generative Aspect Based Sentiment Analysis for Indonesian Language | ICEEI | [Paper](https://doi.org/10.1109/ICEEI59426.2023.10346852) | [Code](https://github.com/rdyzakya/IndoLEGO-ABSA) |
| 2023 | Instruction Tuning for Few-Shot Aspect-Based Sentiment Analysis | ACL-W | [Paper](https://doi.org/10.18653/v1/2023.wassa-1.3) | [Code](https://github.com/amazon-science/instruction-tuning-for-absa) |
| 2023 | MvP: Multi-view Prompting Improves Aspect Sentiment Tuple Prediction | ACL | [Paper](https://doi.org/10.18653/v1/2023.acl-long.240) | [Code](https://github.com/ZubinGou/multi-view-prompting) |
| 2023 | SENER: Sentiment Element Named Entity Recognition for Aspect-Based Sentiment Analysis | ICASSP | [Paper](https://doi.org/10.1109/ICASSP49357.2023.10095101) | - |
| 2023 | Simplifying Aspect-Sentiment Quadruple Prediction with Cartesian Product Operation | ICIC | [Paper](https://doi.org/10.1007/978-981-99-4752-2_58) | - |
| 2023 | Uncertainty-Aware Unlikelihood Learning Improves Generative Aspect Sentiment Quad Prediction | Findings of ACL | [Paper](https://doi.org/10.18653/v1/2023.findings-acl.851) | [Code](https://github.com/byinhao/UAUL) |
| 2024 | A Generative Model-Based Prediction of Aspect-Level Sentiment Quad with Stage Prompts and Semantic Enhancement | ICFTIC | [Paper](https://doi.org/10.1109/ICFTIC64248.2024.10912865) | - |
| 2024 | Adaptive Data Augmentation for Aspect Sentiment Quad Prediction | ICASSP | [Paper](https://doi.org/10.1109/ICASSP48485.2024.10447700) | [Code](https://github.com/wyripple/ada) |
| 2024 | An Instruction Tuning-Based Contrastive Learning Framework for Aspect Sentiment Quad Prediction with Implicit Aspects and Opinions | Findings of EMNLP | [Paper](https://doi.org/10.18653/v1/2024.findings-emnlp.453) | [Code](https://github.com/sydmou/ASQP-ITSCL) |
| 2024 | BvSP: Broad-view Soft Prompting for Few-Shot Aspect Sentiment Quad Prediction | ACL | [Paper](https://doi.org/10.18653/v1/2024.acl-long.460) | [Code](https://github.com/byinhao/BvSP) |
| 2024 | Enhancing Aspect Sentiment Quad Prediction through Dual-Sequence Data Augmentation and Contrastive Learning | ACML | [Search](https://scholar.google.com/scholar?q=Enhancing+Aspect+Sentiment+Quad+Prediction+through+Dual-Sequence+Data+Augmentation+and+Contrastive+Learning) | - |
| 2024 | Enhancing Generative Aspect-Based Sentiment Analysis with Relation-Level Supervision and Prompt | ICASSP | [Paper](https://doi.org/10.1109/ICASSP48485.2024.10448322) | - |
| 2024 | Generative Aspect Sentiment Quad Prediction with Self-Inference Template | MDPI | [Paper](https://doi.org/10.3390/app14146017) | - |
| 2024 | Implicit aspect-based generative model for sentiment analysis based on prompt learning | ICBASE | [Paper](https://doi.org/10.1109/ICBASE63199.2024.10762313) | - |
| 2024 | Improve Chinese Aspect Sentiment Quadruplet Prediction via Instruction Learning Based on Large Generate Models | CMC | [Paper](https://doi.org/10.32604/cmc.2024.047076) | [Code](https://github.com/Wu00zl/MSMT) |
| 2024 | Is Compound Aspect-Based Sentiment Analysis Addressed by LLMs? | Findings of EMNLP | [Paper](https://doi.org/10.18653/v1/2024.findings-emnlp.460) | - |
| 2024 | LLaMA-Based Models for Aspect-Based Sentiment Analysis | WASSA | [Search](https://scholar.google.com/scholar?q=LLaMA-Based+Models+for+Aspect-Based+Sentiment+Analysis) | [Code](https://github.com/biba10/LLaMA-ABSA) |
| 2024 | Make Compound Sentences Simple to Analyze: Learning to Split Sentences for Aspect-based Sentiment Analysis | Findings of EMNLP | [Paper](https://doi.org/10.18653/v1/2024.findings-emnlp.653) | [Code](https://github.com/ryang1119/ATOSS) |
| 2024 | Modeling implicit variable and latent structure for aspect-based sentiment quadruple extraction | Neurocomputing | [Paper](https://doi.org/10.1016/j.neucom.2024.127642) | - |
| 2024 | Permuted Temporal Kolmogorov-Arnold Networks for Stock Price Forecasting Using Generative Aspect-Based Sentiment Analysis | IEEE Access | [Paper](https://doi.org/10.1109/ACCESS.2024.3506658) | - |
| 2024 | Pinpointing Diffusion Grid Noise to Enhance Aspect Sentiment Quad Prediction | Findings of ACL | [Paper](https://doi.org/10.18653/v1/2024.findings-acl.222) | [Code](https://github.com/ch11en/GDP) |
| 2024 | Self-Consistent Reasoning-based Aspect-Sentiment Quad Prediction with Extract-Then-Assign Strategy | Findings of ACL | [Paper](https://doi.org/10.18653/v1/2024.findings-acl.435) | [Code](https://github.com/jieyong99/SCRAP) |
| 2024 | Self-Training with Pseudo-Label Scorer for Aspect Sentiment Quad Prediction | ACL | [Paper](https://doi.org/10.18653/v1/2024.acl-long.640) | [Code](https://github.com/HITSZ-HLT/ST-w-Scorer-ABSA) |
| 2024 | Sentiment Analysis in the Era of Large Language Models: A Reality Check | Findings of NAACL | [Paper](https://doi.org/10.18653/v1/2024.findings-naacl.246) | [Code](https://github.com/DAMO-NLP-SG/LLM-Sentiment) |
| 2024 | Shoes-ACOSI: A Dataset for Aspect-Based Sentiment Analysis with Implicit Opinion Extraction | Findings of EMNLP | [Paper](https://doi.org/10.18653/v1/2024.findings-emnlp.907) | [Code](https://github.com/jpeper/shoes_acosi) |
| 2024 | Unified ABSA via Annotation-Decoupled Multi-Task Instruction Tuning | TKDE | [Paper](https://doi.org/10.1109/TKDE.2024.3392836) | [Code](https://github.com/NUSTM/unifiedabsa) |
| 2025 | $\mathcalS^2$IT: Stepwise Syntax Integration Tuning for Large Language Models in Aspect Sentiment Quad Prediction | Findings of NAACL | [Paper](https://doi.org/10.18653/v1/2025.findings-naacl.379) | [Code](https://github.com/DMIRLAB-Group/S2IT) |
| 2025 | ABCD Team at ASQP-PT 2025: Aspect Sentiment Quad Prediction in Portuguese as Text Generation | IberLEF | [Search](https://scholar.google.com/scholar?q=ABCD+Team+at+ASQP-PT+2025%3A+Aspect+Sentiment+Quad+Prediction+in+Portuguese+as+Text+Generation) | - |
| 2025 | Aspect-Sentiment Quad Prediction with Distilled Large Language Models | RANLP | [Search](https://scholar.google.com/scholar?q=Aspect-Sentiment+Quad+Prediction+with+Distilled+Large+Language+Models) | [Code](https://github.com/FilipposVentirozos/Aspect-Sentiment-Quad-Prediction-with-Distilled-Large-Language-Models) |
| 2025 | Data and Prompt Dual Enhancement for Aspect Sentiment Quad Prediction | ISCTT | [Paper](https://doi.org/10.1109/ISCTT66403.2025.11137908) | - |
| 2025 | Do we still need Human Annotators? Prompting Large Language Models for Aspect Sentiment Quad Prediction | XLLM | [Paper](https://doi.org/10.18653/v1/2025.xllm-1.15) | [Code](https://github.com/NilsHellwig/llm-prompting-asqp) |
| 2025 | Error Comparison Optimization for Large Language Models on Aspect-Based Sentiment Analysis | ACL | [Paper](https://doi.org/10.18653/v1/2025.acl-long.913) | - |
| 2025 | Generative aspect-based sentiment analysis with a grid tagging matching auxiliary task | CSL | [Paper](https://doi.org/10.1016/j.csl.2025.101776) | - |
| 2025 | Graph-enhanced implicit aspect-level sentiment analysis based on multi-prompt fusion | SciRep | [Paper](https://doi.org/10.1038/s41598-025-02609-4) | - |
| 2025 | Intuition meets analytics: Reasoning implicit aspect-based sentiment quadruplets with a dual-system framework | KBS | [Paper](https://doi.org/10.1016/j.knosys.2025.113534) | - |
| 2025 | Leveraging Domain Prediction and Retrieval Augmentation for Cross-domain Aspect Sentiment Quad Prediction | ICFTIC | [Paper](https://doi.org/10.1109/ICFTIC68075.2025.11324636) | - |
| 2025 | MSTDA: Multi-Syntax Template Data Augmentation For Aspect Sentiment Quad Prediction | IJCNN | [Paper](https://doi.org/10.1109/IJCNN64981.2025.11227442) | - |
| 2025 | QAIE: LLM-based Quantity Augmentation and Information Enhancement for few-shot Aspect-Based Sentiment Analysis | IPM | [Paper](https://doi.org/10.1016/j.ipm.2024.103917) | - |
| 2025 | Representative Chain-of-Reasoning Framework for Aspect Sentiment Quad Prediction | ICIC | [Paper](https://doi.org/10.65286/icic.v21i4.56960) | - |
| 2025 | Research on Improved ABSA: Synergistic Effect of Sentence Splitting and Data Enhancement | SEAI | [Paper](https://doi.org/10.1109/SEAI65851.2025.11108877) | - |
| 2025 | SimRP: Syntactic and Semantic Similarity Retrieval Prompting Enhances Aspect Sentiment Quad Prediction | AAI | [Paper](https://doi.org/10.1609/aaai.v39i23.34601) | [Code](https://github.com/jian-projects/simrp) |
| 2025 | Using Review Combination and Pseudo-Tokens for Aspect Sentiment Quad Prediction | Findings of NAACL | [Paper](https://doi.org/10.18653/v1/2025.findings-naacl.214) | [Code](https://github.com/chienarmor/absa-implicit) |
| 2026 | Generative Aspect-Based Sentiment Quadruple Prediction Based on Multi-Order Prompting | TOIS | [Paper](https://doi.org/10.1145/3811909) | - |
| 2026 | Nested Opinion Sextuple Extraction: Design of the Task, Dataset and Extraction Model | TAC | [Paper](https://doi.org/10.1109/TAFFC.2026.3687968) | [Code](https://anonymous.4open.science/r/NOSE-2B5A) |
| 2026 | Vi-AbSQA: Multi-task Prompt Instruction Tuning Model for Vietnamese Aspect-based Sentiment Quadruple Analysis | TALLIP | [Paper](https://doi.org/10.1145/3676886) | - |

### Sequence-to-Tree Prediction (Seq2Tree)

The output is defined as a tree, and the quadruples are read from its nodes or paths.

#### Constrained tree generation

| Year | Title | Venue | Paper | Code |
|---|---|---|---|---|
| 2022 | Aspect-based Sentiment Analysis with Opinion Tree Generation | IJCAI | [Paper](https://doi.org/10.24963/ijcai.2022/561) | - |
| 2022 | Seq2Path: Generating Sentiment Tuples as Paths of a Tree | Findings of ACL | [Paper](https://doi.org/10.18653/v1/2022.findings-acl.174) | - |
| 2023 | Exploring Graph Pre-training for Aspect-based Sentiment Analysis | Findings of EMNLP | [Paper](https://doi.org/10.18653/v1/2023.findings-emnlp.234) | [Code](https://github.com/HoraceXIaoyiBao/EGP4ABSA-EMNLP2023) |
| 2024 | Transition-based Opinion Generation for Aspect-based Sentiment Analysis | Findings of ACL | [Paper](https://doi.org/10.18653/v1/2024.findings-acl.182) | - |
| 2025 | Enhancing aspect sentiment quad prediction with syntactic information in generation model | FoCS | [Paper](https://doi.org/10.1007/s11704-025-40940-1) | - |
| 2025 | Exploring Hybrid Sampling Inference for Aspect-based Sentiment Analysis | Findings of NAACL | [Paper](https://doi.org/10.18653/v1/2025.findings-naacl.236) | - |

#### Chart parsing

| Year | Title | Venue | Paper | Code |
|---|---|---|---|---|
| 2023 | Opinion Tree Parsing for Aspect-based Sentiment Analysis | Findings of ACL | [Paper](https://doi.org/10.18653/v1/2023.findings-acl.505) | [Code](https://github.com/HoraceXIaoyiBao/OTP4ABSA-ACL2023) |
| 2026 | Exploring Context-Free Opinion Grammar for Aspect-Based Sentiment Analysis | TKDE | [Paper](https://doi.org/10.1109/TKDE.2025.3632628) | [Code](https://github.com/HoraceXIaoyiBao/OTP4ABSA-ACL2023) |

#### Tree-slot classification

| Year | Title | Venue | Paper | Code |
|---|---|---|---|---|
| 2026 | Opinion-Tree-Aware Prompt Tuning for Aspect Sentiment Quadruple Prediction | ICASSP | [Paper](https://doi.org/10.1109/ICASSP55912.2026.11460901) | - |

### Pipeline

Separately trained or prompted stages pass a discrete intermediate result to the final stage.

#### Discriminative final stage

| Year | Title | Venue | Paper | Code |
|---|---|---|---|---|
| 2021 | Aspect-Category-Opinion-Sentiment Quadruple Extraction with Implicit Aspects and Opinions | ACL | [Paper](https://doi.org/10.18653/v1/2021.acl-long.29) | [Code](https://github.com/NUSTM/ACOS) |
| 2021 | Comparative Opinion Quintuple Extraction from Product Reviews | EMNLP | [Paper](https://doi.org/10.18653/v1/2021.emnlp-main.322) | [Code](https://github.com/NUSTM/COQE) |
| 2022 | Complete quadruple extraction using a two-stage neural model for aspect-based sentiment analysis | Neurocomputing | [Paper](https://doi.org/10.1016/j.neucom.2022.04.027) | [Code](https://github.com/PrayChen/Aspect_sentiment_quadruple_extraction_data) |
| 2023 | Enhancing aspect-based sentiment analysis with dependency-attention GCN and mutual assistance mechanism | JIIS | [Paper](https://doi.org/10.1007/s10844-023-00811-2) | - |
| 2024 | Aspect-Category-Opinion-Sentiment Quadruple Extraction for Code Mixed Data | ICDAM | [Search](https://scholar.google.com/scholar?q=Aspect-Category-Opinion-Sentiment+Quadruple+Extraction+for+Code+Mixed+Data) | - |
| 2025 | Dialogues Aspect-based Sentiment Quadruple Extraction via Structural Entropy Minimization Partitioning | CIKM | [Paper](https://doi.org/10.1145/3746252.3761060) | [Code](https://github.com/KunPunCN/SEMDia/) |
| 2025 | SetFitQuad: A Few-Shot Framework for Aspect Sentiment Quad Prediction With Sampling Strategies | IEEE Access | [Paper](https://doi.org/10.1109/ACCESS.2025.3600351) | [Code](https://github.com/HsiuMin/SetFitQuad-Code) |
| 2025 | Urdu Aspect-Category-Opinion-Sentiment (UACOS) Quadruple Extraction: A Transfer Learning Approach | C-CODE | [Paper](https://doi.org/10.1109/C-CODE67372.2025.11204128) | - |

#### Generative final stage

| Year | Title | Venue | Paper | Code |
|---|---|---|---|---|
| 2023 | Two-Stage Aspect Sentiment Quadruple Prediction Based on MRC and Text Generation | IEEE SMC | [Paper](https://doi.org/10.1109/SMC53992.2023.10394369) | [Code](https://github.com/SlienceLZJ/ASQP) |
| 2024 | A Hybrid Approach to Dimensional Aspect-Based Sentiment Analysis Using BERT and Large Language Models | MDPI | [Paper](https://doi.org/10.3390/electronics13183724) | - |
| 2024 | A Sentiment Analysis Model Based on Text Generation-OpnionSpanT5 | ICCECT | [Paper](https://doi.org/10.1109/ICCECT60629.2024.10546142) | - |
| 2025 | Aligning Black-Box LLMs for Aspect Sentiment Quad Prediction | Findings of EMNLP | [Paper](https://doi.org/10.18653/v1/2025.findings-emnlp.53) | - |
| 2025 | Dynamic Order Template Prediction for Generative Aspect-Based Sentiment Analysis | ACL | [Paper](https://doi.org/10.18653/v1/2025.acl-short.48) | [Code](https://github.com/yonghyun010102/DOT) |
| 2025 | E2TP: Element to tuple prompting improves aspect sentiment tuple prediction | NN | [Paper](https://doi.org/10.1016/j.neunet.2025.107847) | [Code](https://github.com/mghiasvand1/E2TP) |
| 2025 | Sentimental Image Generation for Aspect-based Sentiment Analysis | Findings of ACL | [Paper](https://doi.org/10.18653/v1/2025.findings-acl.210) | [Code](https://github.com/HoraceXIaoyiBao/ACL25-SIG4ABSA) |
| 2026 | E-ABSA20K: A Dataset and Propose-and-Verify for Aspect-Based Sentiment Analysis in Long E-commerce Reviews | Findings of ACL | [Paper](https://doi.org/10.18653/v1/2026.findings-acl.892) | - |
| 2026 | Sentimental image generation with image quality assessment | PR | [Paper](https://doi.org/10.1016/j.patcog.2026.113269) | - |

## Datasets

The datasets below are discussed in the survey. Quadruple datasets come first in each table, followed by variants with other tuples. The first eight rows of the open table (13 datasets) are the ones that the survey checks for repeated quadruples (Table II of the paper).

### Open datasets

Datasets with a public download link.

| Dataset | Tuple | Domain | Language | Unit | Paper | Data | Note |
|---|---|---|---|---|---|---|---|
| Rest15, Rest16 | (c, a, o, s) | Restaurant | English | Sentence | [2021](https://doi.org/10.18653/v1/2021.emnlp-main.726) | [Link](https://github.com/IsakZhang/ABSA-QUAD) |  |
| Restaurant-ACOS, Laptop-ACOS | (c, a, o, s) | Restaurant, laptop | English | Sentence | [2021](https://doi.org/10.18653/v1/2021.acl-long.29) | [Link](https://github.com/NUSTM/ACOS) |  |
| en-Phone, zh-FoodBeverage | (c, a, o, s) | Phone, food and beverage | English, Chinese | Review | [2023](https://doi.org/10.18653/v1/2023.findings-acl.777) | [Link](https://github.com/Datastory-CN/ASQP-Datasets) |  |
| FSQP | (c, a, o, s) | Restaurant, hotel, beauty | English | Sentence | [2024](https://doi.org/10.18653/v1/2024.acl-long.460) | [Link](https://github.com/byinhao/BvSP) | Few-shot splits with unseen categories |
| OATS (Amazon FineFood, Coursera, Hotels) | (c, a, o, s) | Fine food, online courses, hotel | English | Sentence | [2024, search](https://scholar.google.com/scholar?q=OATS%3A+A+Challenge+Dataset+for+Opinion+Aspect+Target+Sentiment+Joint+Detection+for+Aspect-Based+Sentiment+Analysis) | [Link](https://github.com/RiTUAL-MBZUAI/OATS-ABSA) |  |
| Shoes-ACOSI | (c, a, o, s, i) | Footwear | English | Paragraph | [2024](https://doi.org/10.18653/v1/2024.findings-emnlp.907) | [Link](https://github.com/jpeper/shoes_acosi) | Fifth element: direct or implied opinion |
| Hospitality (ACOS-Hotel) | (c, a, o, s) | Hotel | English | Sentence | [2025](https://doi.org/10.1007/978-981-96-0579-8_8) | [Link](https://github.com/marwahalharbi2/QuadABSA-TourismDataset) |  |
| MEMD-ABSA | (c, a, o, s) | Books, clothing, hotel, laptop, restaurant | English | Sentence | [2025](https://doi.org/10.1007/s10579-025-09820-9) | [Link](https://github.com/NUSTM/MEMD-ABSA) |  |
| DiaASQ | (t, a, o, s) | Mobile phone | Chinese, English | Dialogue | [2023](https://doi.org/10.18653/v1/2023.findings-acl.849) | [Link](https://github.com/unikcc/DiaASQ) | Target instead of category |
| SIGHAN-2024 dimABSA | (c, a, o, valence, arousal) | Restaurant | Chinese | Sentence | [2024, search](https://scholar.google.com/scholar?q=Overview+of+the+SIGHAN+2024+shared+task+for+Chinese+dimensional+aspect-based+sentiment+analysis) | [Link](https://github.com/NYCU-NLP/SIGHAN2024-dimABSA) | Real-valued sentiment |
| ASQP-PT | (c, a, o, s) | Hotel | Portuguese | Paragraph | [2025, search](https://scholar.google.com/scholar?q=Overview+of+ASQP-PT+at+IberLEF+2025%3A+Overview+of+the+Task+on+Aspect-Sentiment+Quadruple+Prediction+in+Portuguese) | [Link](https://sites.google.com/inf.ufpel.edu.br/asqp-pt-2025/data) | Shared task data |
| KurdABSA | (c, a, o, s) | Restaurant | Sorani Kurdish | Sentence | [2025](https://doi.org/10.1016/j.dib.2025.112012) | [Link](https://data.mendeley.com/datasets/h5t7p4bcj2/1) |  |
| COQE (Camera, Car, Ele) | (subject, object, aspect, opinion, preference) | Camera, car, electronics | English, Chinese | Sentence | [2021](https://doi.org/10.18653/v1/2021.emnlp-main.322) | [Link](https://github.com/NUSTM/COQE) | Comparative quintuples |
| QAM | (claim, evidence, evidence type, stance) | Argument | English | Document | [2023](https://doi.org/10.18653/v1/2023.findings-acl.59) | [Link](https://github.com/guojiapub/QuadTAG) | Argument quadruples; data in data/QAM |

### Non-open datasets

Datasets without a public download link at the time of writing. Some may be available from the authors on request.

| Dataset | Tuple | Domain | Language | Unit | Paper | Note |
|---|---|---|---|---|---|---|
| UACOS-Rest, UACOS-Laptop | (c, a, o, s) | Restaurant, laptop | Urdu | Sentence | [2025](https://doi.org/10.1109/C-CODE67372.2025.11204128) |  |
| Hinglish-ACOS | (c, a, o, s) | Mobile phone | Hindi-English code-mixed | Sentence | [2024, search](https://scholar.google.com/scholar?q=Aspect-Category-Opinion-Sentiment+Quadruple+Extraction+for+Code+Mixed+Data) |  |
| Vi-AbSQA | (c, a, o, s) | Restaurant | Vietnamese | Sentence | [2026](https://doi.org/10.1145/3676886) |  |
| FIN-ASQP | (c, a, o, s) | Financial news | Indonesian | Sentence | [2024](https://doi.org/10.1109/ACCESS.2024.3506658) |  |
| CCD-ASQP | (c, a, o, s) | Multi-domain | Chinese | Sentence | [2025](https://doi.org/10.1109/ICFTIC68075.2025.11324636) | Cross-domain |
| E-ABSA | (c, a, o, s) | Bags, dresses, cosmetics, furniture | English | Paragraph | [2026](https://doi.org/10.18653/v1/2026.findings-acl.892) | Long e-commerce reviews, LLM-assisted labels |
| Zh-Agriculture | (c, a, o, s) | Agricultural products | Chinese | Sentence | [2023](https://doi.org/10.32604/cmc.2023.037060) |  |
| ZhASQP | (c, a, o, s) | Agricultural products | Chinese | Sentence | [2024](https://doi.org/10.32604/cmc.2024.047076) | The code repository holds no data files |
| NOSE | Nested sextuples | Social media | English, Chinese | Document | [2026](https://doi.org/10.1109/TAFFC.2026.3687968) | Anonymous review link only, no files visible |
| MABSA (multimodal) | (c, a, s) with image region | Restaurant | English | Sentence + image | [2025](https://doi.org/10.1002/asi.70026) | No opinion term |
| FlightABSA | (c, a, o, s) | Airline | English | Sentence | [2025](https://doi.org/10.18653/v1/2025.xllm-1.15) | Not publicly released |

Tuple notation: c = aspect category, a = aspect term, o = opinion term, s = sentiment polarity, t = target, i = implicit-opinion indicator.

## Citation

If you find this repository useful, please cite our survey. The BibTeX entry will be added after publication.
