# Literature Review – BharatNLP

## 1. Introduction

Multimodal emotion and sentiment analysis is an active research area in Artificial Intelligence. It combines information from different modalities, such as text, speech and facial-expression features, to analyse emotion-related signals.

For BharatNLP, the literature review focuses on four major research areas:

- Hindi-English code-mixed Natural Language Processing (NLP).
- Multimodal emotion recognition and fusion.
- Missing-modality handling and adaptive fusion.
- Uncertainty estimation and explainable predictions.

The objective is to study existing research, understand its methodologies and limitations, identify research gaps, and establish a technically grounded research direction for BharatNLP.

---

## 2. Review of Existing Research

### Paper 1: SemEval-2020 Task 9 – Sentiment Analysis of Code-Mixed Tweets

- **Authors:** Parth Patwa, Gustavo Aguilar, Sudipta Kar, Suraj Pandey, Srinivas PYKL, Björn Gambäck, Tanmoy Chakraborty, Thamar Solorio and Amitava Das.
- **Year:** 2020
- **Research area:** Hindi-English and Spanish-English code-mixed sentiment analysis.
- **Dataset:** SentiMix 2020, containing approximately 20,000 Hinglish tweets and 19,000 Spanglish tweets.
- **Approach:** The task introduced code-mixed datasets annotated with word-level language identification and sentence-level sentiment labels. The sentiment classes are Positive, Negative and Neutral.
- **Key findings:** The best reported F1 scores in the shared task were 75.0% for Hinglish and 80.6% for Spanglish. BERT-based models and ensemble approaches were among the successful approaches.
- **Limitations:** The dataset focuses on tweets and three sentiment classes. It does not provide detailed emotion labels or audio and visual information.
- **Relevance to BharatNLP:** Provides a benchmark for developing and evaluating the Hinglish text-processing module, especially for Roman-script Hindi and code-mixed expressions.
- **Reference:** https://aclanthology.org/2020.semeval-1.100/

### Paper 2: Multitasking of Sentiment Detection and Emotion Recognition in Code-Mixed Hinglish Data

- **Authors:** Soumitra Ghosh, Amit Priyankar, Asif Ekbal and Pushpak Bhattacharyya.
- **Year:** 2023
- **Research area:** Joint sentiment detection and emotion recognition in Hinglish.
- **Dataset:** A manually emotion-annotated version of the 20,000-instance Hinglish SentiMix dataset.
- **Approach:** Uses cross-lingual transfer learning and XLM-RoBERTa representations in a multitask learning framework. The system jointly learns sentiment and emotion-related classification using shared representations and task-specific outputs.
- **Emotion categories:** Anger, Disgust, Fear, Joy, Sadness, Surprise and Others.
- **Key findings:** The paper reports that multitask learning and transfer learning improve code-mixed sentiment analysis performance compared with the evaluated single-task approaches. The reported best sentiment F1 score is 71.61%.
- **Limitations:** The dataset has class imbalance, particularly for some less frequent emotion categories. The work is text-based and does not include audio or visual modalities.
- **Relevance to BharatNLP:** Supports the development of a multilingual text module that handles sentiment and emotion-related classification together. It also highlights the importance of class imbalance and transfer learning.
- **Reference:** https://doi.org/10.1016/j.knosys.2022.110182

### Paper 3: Multimodal Prompt Learning with Missing Modalities for Sentiment Analysis and Emotion Recognition

- **Authors:** Zirun Guo, Tao Jin and Zhou Zhao.
- **Year:** 2024
- **Research area:** Multimodal learning with incomplete or missing input modalities.
- **Approach:** Introduces Multimodal Prompt Learning with Missing Modalities (MPLMM). It uses three types of prompts:
  - Generative prompts to estimate representations of missing modalities.
  - Missing-signal prompts to distinguish original and generated modality representations.
  - Missing-type prompts to represent which modality is unavailable.
- **Datasets:** CMU-MOSEI, CMU-MOSI, IEMOCAP and CH-SIMS.
- **Key findings:** The proposed method is evaluated against missing-modality baselines and demonstrates the potential of prompt-based learning for multimodal tasks with incomplete inputs.
- **Limitations:** The method operates on learned modality representations and does not directly solve every practical problem associated with missing raw audio, video or text streams. Its datasets also do not directly establish performance on Hindi-English code-mixed data.
- **Relevance to BharatNLP:** Provides a research foundation for handling unavailable modalities. BharatNLP can initially implement available-modality fusion and later investigate representation generation and missing-modality prompts as advanced experiments.
- **Reference:** https://aclanthology.org/2024.acl-long.94/
- **Official code:** https://github.com/zrguo/MPLMM

### Paper 4: COLD Fusion – Calibrated and Ordinal Latent Distribution Fusion for Uncertainty-Aware Multimodal Emotion Recognition

- **Authors:** Mani Kumar Tellamekala, Shahin Amiriparian, Björn W. Schuller, Elisabeth André, Timo Giesbrecht and Michel Valstar.
- **Year:** 2024
- **Research area:** Uncertainty-aware audio-visual emotion recognition.
- **Approach:** Introduces an uncertainty-aware fusion framework that learns latent distributions over unimodal temporal representations. It uses two important constraints:
  - Calibration: Makes modality-wise uncertainty estimates meaningful in relation to prediction errors.
  - Ordinal Ranking: Encourages uncertainty estimates to preserve the relative ordering of more and less informative modality inputs.
- **Technical contribution:** The paper jointly applies these constraints using a softmax distributional matching loss.
- **Datasets:** AVEC 2019 CES, CMU-MOSEI and IEMOCAP.
- **Key findings:** The authors report improvements in generalisation, predictive uncertainty estimation and robustness to novel noise patterns in their evaluated experiments.
- **Limitations:** The original work focuses on audio and visual modalities, not a complete text-audio-visual system. Its approach would require adaptation and evaluation before being applied to BharatNLP's three-modality architecture.
- **Relevance to BharatNLP:** Provides a research direction for modality-wise uncertainty estimation, calibrated predictions and reliability-aware fusion.
- **Reference:** https://doi.org/10.1109/TPAMI.2023.3325770

### Paper 5: SentiGrad – A New Hindi-English Code Mixed Sentiment Analysis Dataset with Preliminary Results and Open Challenges

- **Authors:** P. S. Ghosh and S. Sengupta.
- **Year:** 2024
- **Research area:** Hindi-English code-mixed sentiment analysis.
- **Dataset:** SentiGrad, containing Hindi-English code-mixed comments from Indian learners on graduate-level educational courses hosted on popular YouTube channels.
- **Approach:** Introduces a dataset annotated into Positive, Negative and Neutral sentiment classes by five independent annotators. The paper also presents preliminary machine learning, deep learning and NLP baseline experiments.
- **Key findings:** Highlights the importance of specialised code-mixed datasets for analysing Indian learners' feedback and discusses open challenges in code-mixed sentiment analysis.
- **Limitations:** It focuses on educational comments and sentiment classification rather than detailed emotion recognition or multimodal analysis.
- **Relevance to BharatNLP:** Offers an India-focused dataset candidate for exploring code-mixed language patterns and sentiment analysis beyond social-media tweets.
- **Reference:** https://doi.org/10.1109/DABCon63472.2024.10919296

### Paper 6: MELD – A Multimodal Multi-Party Dataset for Emotion Recognition in Conversations

- **Authors:** Soujanya Poria, Devamanyu Hazarika, Navonil Majumder, Gautam Naik, Erik Cambria and Rada Mihalcea.
- **Year:** 2019
- **Research area:** Multimodal emotion recognition in multi-party conversations.
- **Dataset:** Multimodal EmotionLines Dataset (MELD), containing approximately 13,000 utterances from 1,433 dialogues from the television series Friends.
- **Modalities:** Text, audio and visual information are available for the utterances.
- **Emotion categories:** Anger, Disgust, Fear, Joy, Sadness, Surprise and Neutral.
- **Sentiment categories:** Positive, Negative and Neutral.
- **Approach:** The paper introduces a multimodal multi-party conversational dataset and evaluates multimodal baselines. It demonstrates the importance of conversational context and multiple modalities for emotion recognition.
- **Key findings:** Combining contextual and multimodal information can improve emotion recognition in conversations compared with relying on isolated information alone.
- **Limitations:** The dataset is based on English-language television conversations. Its domain, speaker behaviour and cultural context may not generalise directly to real-world Indian conversations or Hinglish inputs.
- **Relevance to BharatNLP:** Provides a useful benchmark candidate for understanding aligned text, audio and visual information, multimodal experiments and contextual modelling.
- **Reference:** https://aclanthology.org/P19-1050/
- **Dataset website:** https://affective-meld.github.io/

---

## 3. Comparative Analysis of Existing Research

| Research paper | Primary focus | Modalities | Main contribution |
|---|---|---|---|
| SemEval-2020 Task 9 | Code-mixed sentiment | Text | Hinglish and Spanglish sentiment benchmark |
| Ghosh et al. (2023) | Hinglish multitask learning | Text | Joint sentiment and emotion classification |
| MPLMM (2024) | Missing modalities | Multimodal | Prompt-based missing-modality handling |
| COLD Fusion (2024) | Uncertainty-aware fusion | Audio + Visual | Calibration and ordinal uncertainty ranking |
| SentiGrad (2024) | Indian learner sentiment | Text | Educational-domain Hinglish dataset |
| MELD (2019) | Conversational emotion recognition | Text + Audio + Visual | Multimodal multi-party conversational dataset |

### Key Observations

1. Code-mixed NLP research provides useful foundations for Hindi-English sentiment analysis.
2. Multitask learning can support the joint modelling of sentiment and emotion-related labels.
3. Multimodal datasets demonstrate the value of combining text, audio and visual information.
4. Missing-modality research provides techniques for handling incomplete multimodal inputs.
5. Uncertainty-aware fusion can help distinguish informative inputs from less reliable ones.
6. Existing datasets differ in language, domain, annotation scheme and modality availability. They cannot automatically be combined into one aligned training dataset.

---

## 4. Research Gap and Challenges

Based on the reviewed research, the following areas deserve further investigation:

### 4.1 Code-Mixed Language Processing

Handling Hindi, English and Hinglish, including Roman-script Hindi, spelling variations, informal expressions and language switching.

### 4.2 Multimodal Reliability

Text, audio and visual inputs may have different levels of quality and usefulness. The fusion mechanism should account for these differences.

### 4.3 Missing Modalities

Real-world applications may not always receive all three inputs. The system should be able to operate using the available modalities without assuming that every input is present.

### 4.4 Cross-Modal Disagreement

Different modalities may provide conflicting emotion-related predictions. The system should identify such disagreements instead of blindly combining all predictions.

### 4.5 Explainability

Users should be able to understand which modality and which observable features contributed to an output.

### 4.6 Uncertainty Estimation

The system should communicate uncertainty and avoid presenting every prediction as equally reliable.

### 4.7 Domain and Language Generalisation

Models trained on English television conversations, social-media tweets or educational comments may not generalise directly to Indian real-world conversations. Evaluation across different language and domain conditions is necessary.

These are research directions rather than claims that existing systems cannot address them. Further literature review and empirical comparisons will be necessary.

---

## 5. Proposed Research Direction for BharatNLP

BharatNLP will explore an India-focused multimodal emotion intelligence platform with three independent processing modules.

### 5.1 Text Module

- Hindi-English-Hinglish text processing.
- Sentiment and emotion-related classification.
- Handling Roman-script Hindi, code-mixing and informal expressions.
- Context-aware text analysis where suitable.

### 5.2 Audio Module

- Speech-to-text transcription.
- Acoustic feature extraction.
- Speech emotion-related classification.
- Handling noisy and incomplete audio inputs.

### 5.3 Vision Module

- Face detection and facial landmark extraction.
- Visible facial-expression feature analysis.
- Facial-expression classification.
- Handling poor lighting, occlusion and low-quality frames.

### 5.4 Multimodal Fusion Module

The outputs of the three independent modules will be combined through an adaptive fusion mechanism.

The project will investigate:

- Reliability-aware adaptive fusion.
- Handling unavailable and low-quality modalities.
- Detecting disagreement between modality predictions.
- Uncertainty-aware prediction and calibration.
- Explainable predictions.
- Comparison of conventional and adaptive fusion approaches.

### 5.5 Conversational Application

The final application will integrate the independent modules through a backend and frontend interface. It will accept supported text, audio and webcam inputs and present emotion-related signal analysis with appropriate explanations and uncertainty information.

The system will describe observable language, acoustic and facial-expression patterns rather than claiming to identify a person's true internal emotional state.

---

## 6. Proposed Experimental and Evaluation Plan

The system will be evaluated using suitable datasets, baselines and metrics for each task.

| Evaluation area | Possible metrics or experiments |
|---|---|
| Classification | Accuracy, Precision, Recall, Macro-F1 |
| Class imbalance | Per-class Precision, Recall and F1 |
| Prediction reliability | Expected Calibration Error (ECE), Brier Score |
| Robustness | Performance under noisy and missing inputs |
| Fusion | Unimodal versus conventional and adaptive fusion |
| Disagreement | Performance and behaviour under cross-modal conflicts |
| Explainability | Qualitative and consistency analysis of explanations |
| Efficiency | Inference latency and resource usage |

### Planned Experiments

1. Text-only, audio-only and vision-only baselines.
2. Conventional late-fusion baseline.
3. Reliability-aware adaptive fusion.
4. Missing-modality experiments using different available-input combinations.
5. Low-quality and noisy-input experiments.
6. Cross-modal disagreement analysis.
7. Calibration and uncertainty evaluation.
8. Ablation studies to understand the contribution of individual modules.

Comparisons will use consistent data splits and evaluation conditions wherever possible.

---

## 7. Dataset Strategy

The reviewed papers provide several candidate datasets for different modules.

| Dataset | Potential use | Important consideration |
|---|---|---|
| SentiMix | Hinglish sentiment classification | Tweet-based, three sentiment labels |
| Emotion-annotated SentiMix | Hinglish emotion and sentiment | Class imbalance |
| SentiGrad | Indian educational-domain sentiment | Domain-specific comments |
| MELD | Multimodal conversational experiments | English television conversations |
| CMU-MOSEI | Multimodal sentiment and emotion research | Dataset labels and modality alignment must be checked |
| IEMOCAP | Audio-visual emotion experiments | Access conditions and label mapping must be checked |
| RAF-DB / FER-2013 | Facial-expression classification | Visual-only datasets; not aligned with text and audio |

### Dataset Integration Considerations

- Independent text, audio and visual datasets are not automatically aligned.
- Emotion labels may differ across datasets.
- Dataset licenses and access requirements must be checked before use.
- Training, validation and testing splits should avoid data leakage.
- A separate consent-based pilot dataset may be considered for testing real-world Indian usage.

---

## 8. Research Contributions to Investigate

Based on the reviewed literature, BharatNLP will investigate the following proposed contributions:

1. India-focused Hindi-English-Hinglish text analysis.
2. A unified application integrating text, audio and visual signal analysis.
3. Reliability-aware adaptive fusion across available modalities.
4. Handling missing and low-quality inputs.
5. Cross-modal disagreement detection.
6. Explainable and uncertainty-aware outputs.
7. Evaluation under different language, noise and modality conditions.

These are proposed project contributions and research hypotheses. Their novelty and effectiveness must be established through further literature review, implementation and experiments.

---

## 9. Conclusion

The reviewed literature establishes useful foundations for BharatNLP across code-mixed NLP, multitask sentiment and emotion classification, multimodal conversational analysis, missing-modality learning and uncertainty-aware fusion.

SentiMix and SentiGrad provide relevant directions for Hindi-English text processing. The Hinglish multitask learning study demonstrates the potential of jointly modelling sentiment and emotion-related labels. MELD provides a multimodal conversational benchmark, while MPLMM and COLD Fusion offer research directions for missing-modality handling and uncertainty-aware fusion.

BharatNLP will build upon these approaches and investigate their integration into an India-focused multimodal application. Its performance, robustness and research novelty will be established through systematic experiments rather than assumed in advance.

---

## 10. References

1. Patwa, P. et al. (2020). *SemEval-2020 Task 9: Overview of Sentiment Analysis of Code-Mixed Tweets.* https://aclanthology.org/2020.semeval-1.100/

2. Ghosh, S., Priyankar, A., Ekbal, A. and Bhattacharyya, P. (2023). *Multitasking of Sentiment Detection and Emotion Recognition in Code-Mixed Hinglish Data.* https://doi.org/10.1016/j.knosys.2022.110182

3. Guo, Z., Jin, T. and Zhao, Z. (2024). *Multimodal Prompt Learning with Missing Modalities for Sentiment Analysis and Emotion Recognition.* https://aclanthology.org/2024.acl-long.94/

4. Tellamekala, M. K. et al. (2024). *COLD Fusion: Calibrated and Ordinal Latent Distribution Fusion for Uncertainty-Aware Multimodal Emotion Recognition.* https://doi.org/10.1109/TPAMI.2023.3325770

5. Ghosh, P. S. and Sengupta, S. (2024). *SentiGrad: A New Hindi-English Code Mixed Sentiment Analysis Dataset with Preliminary Results and Open Challenges.* https://doi.org/10.1109/DABCon63472.2024.10919296

6. Poria, S. et al. (2019). *MELD: A Multimodal Multi-Party Dataset for Emotion Recognition in Conversations.* https://aclanthology.org/P19-1050/
