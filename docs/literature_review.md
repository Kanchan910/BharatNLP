# Literature Review – BharatNLP

## 1. Introduction

Multimodal emotion and sentiment analysis is an active research area in Artificial Intelligence. It combines information from different modalities, such as text, speech and facial-expression features, to understand emotion-related signals.

For BharatNLP, the literature review focuses on three major areas:

- Hindi-English code-mixed NLP.
- Multimodal emotion recognition and fusion.
- Missing-modality handling and uncertainty-aware prediction.

The objective is to understand existing research, identify its limitations and establish a research direction for BharatNLP.

## 2. Review of Existing Research

### Paper 1: SemEval-2020 Task 9 – Sentiment Analysis of Code-Mixed Tweets
- **Authors:** Patwa et al.
- **Year:** 2020
- **Research area:** Hindi-English code-mixed sentiment analysis.
- **Approach:** Introduced the SentiMix dataset containing Hinglish and Spanglish tweets with sentiment labels.
- **Relevance:** Provides a useful benchmark for developing BharatNLP's Hinglish text-processing module.
- **Reference:** https://aclanthology.org/2020.semeval-1.100/

### Paper 2: Multitasking of Sentiment Detection and Emotion Recognition in Code-Mixed Hinglish Data
- **Authors:** Ghosh et al.
- **Year:** 2023
- **Research area:** Joint sentiment and emotion recognition in Hinglish.
- **Approach:** Uses cross-lingual transfer learning and XLM-R-based representations for sentiment and emotion classification.
- **Relevance:** Supports the idea of developing a Hindi-English NLP module that handles both sentiment and emotion-related labels.
- **Reference:** https://doi.org/10.1016/j.knosys.2022.110182

### Paper 3: Multimodal Prompt Learning with Missing Modalities for Sentiment Analysis and Emotion Recognition
- **Authors:** Guo, Jin and Zhao.
- **Year:** 2024
- **Research area:** Multimodal learning with incomplete inputs.
- **Approach:** Uses generative, missing-signal and missing-type prompts to handle unavailable modalities.
- **Relevance:** Provides research direction for BharatNLP's missing-modality handling and adaptive fusion experiments.
- **Reference:** https://aclanthology.org/2024.acl-long.94/

### Paper 4: COLD Fusion – Calibrated and Ordinal Latent Distribution Fusion for Uncertainty-Aware Multimodal Emotion Recognition
- **Authors:** Tellamekala et al.
- **Year:** 2024
- **Research area:** Uncertainty-aware multimodal emotion recognition.
- **Approach:** Estimates modality-wise uncertainty and uses calibrated latent distributions during fusion.
- **Relevance:** Helps guide BharatNLP's reliability-aware fusion and uncertainty estimation.
- **Reference:** https://doi.org/10.1109/TPAMI.2023.3325770

### Paper 5: SentiGrad – A New Hindi-English Code Mixed Sentiment Analysis Dataset with Preliminary Results and Open Challenges
- **Authors:** Ghosh and Sengupta.
- **Year:** 2024
- **Research area:** Hindi-English code-mixed sentiment analysis.
- **Approach:** Introduces a dataset of comments from Indian learners, annotated as positive, negative and neutral.
- **Relevance:** A potentially useful India-focused resource for exploring code-mixed language challenges.
- **Reference:** https://doi.org/10.1109/DABCon63472.2024.10919296

## 3. Research Gaps and Challenges

Based on this initial literature review, the following areas deserve further investigation:

1. **Code-mixed language processing:** Handling Hindi, English and Hinglish, including Roman-script Hindi, spelling variations and informal expressions.
2. **Multimodal reliability:** Audio, text and visual signals may have different levels of quality and usefulness.
3. **Missing modalities:** Real-world applications may not always receive all three inputs.
4. **Cross-modal disagreement:** Different modalities may provide conflicting emotion-related predictions.
5. **Explainability:** Users should be able to understand which signals contributed to a prediction.
6. **Uncertainty estimation:** The system should communicate when its predictions are uncertain instead of presenting every output as reliable.

These are research directions, not claims that existing systems cannot address them. A deeper comparison of methods and experiments will be required.

## 4. Proposed Research Direction for BharatNLP

BharatNLP will explore an India-focused multimodal emotion intelligence platform with three independent processing modules:

- **Text Module:** Hindi-English-Hinglish sentiment and emotion-related classification.
- **Audio Module:** Speech transcription and acoustic emotion-related classification.
- **Vision Module:** Facial-expression feature analysis and classification.

The outputs of these modules will be combined through a multimodal fusion mechanism.

The proposed system will investigate:

- Reliability-aware adaptive fusion.
- Handling unavailable or low-quality modalities.
- Detecting disagreement between modality predictions.
- Explainable predictions and uncertainty estimates.
- Evaluation across different language and modality conditions.

The system will describe observable language, acoustic and facial-expression patterns rather than claiming to identify a person's true internal emotional state.

## 5. Evaluation Plan

The proposed system will be evaluated using appropriate metrics for each task.

| Evaluation area | Possible metrics |
|---|---|
| Classification | Accuracy, Precision, Recall, Macro-F1 |
| Prediction reliability | Calibration error, Brier Score |
| Robustness | Performance under noisy or missing inputs |
| Fusion | Comparison of unimodal and multimodal performance |
| Efficiency | Inference latency |

Experiments will compare text-only, audio-only, vision-only, conventional fusion and adaptive fusion approaches under comparable conditions.

## 6. Conclusion

The initial literature review indicates that code-mixed NLP, multimodal fusion, missing-modality handling and uncertainty estimation are important research areas for BharatNLP.

The project will build upon existing research and investigate how these approaches can be integrated into a practical India-focused application. Further paper reading, dataset verification and baseline experiments will be necessary before making claims about research novelty or performance.

## 7. References

1. Patwa et al. (2020), SemEval-2020 Task 9. https://aclanthology.org/2020.semeval-1.100/
2. Ghosh et al. (2023), Multitasking of Sentiment Detection and Emotion Recognition in Code-Mixed Hinglish Data. https://doi.org/10.1016/j.knosys.2022.110182
3. Guo et al. (2024), Multimodal Prompt Learning with Missing Modalities. https://aclanthology.org/2024.acl-long.94/
4. Tellamekala et al. (2024), COLD Fusion. https://doi.org/10.1109/TPAMI.2023.3325770
5. Ghosh and Sengupta (2024), SentiGrad. https://doi.org/10.1109/DABCon63472.2024.10919296