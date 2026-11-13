# BharatNLP – System Architecture

## 1. Introduction

BharatNLP follows a modular multimodal AI architecture that integrates Natural Language Processing, Speech Emotion Recognition and Computer Vision.

The system is designed to process text, audio and visual inputs independently or together. Individual AI modules generate structured predictions, which are combined through an adaptive multimodal fusion mechanism.

The architecture also investigates missing-modality handling, input-quality assessment, cross-modal disagreement detection, uncertainty estimation and explainable predictions.

The overall objective is to develop an India-focused multimodal application supporting Hindi, English and Hinglish inputs.

---

## 2. High-Level Architecture

```text
                         USER
                           |
                           v
                    REACT FRONTEND
                           |
             TEXT / AUDIO / IMAGE / VIDEO
                           |
                           v
                    FASTAPI BACKEND
                           |
                    INPUT VALIDATION
                           |
                  INPUT QUALITY CHECK
                           |
          +----------------+----------------+
          |                |                |
          v                v                v
      TEXT MODULE      AUDIO MODULE      VISION MODULE
          |                |                |
          v                v                v
      TEXT NLP         SPEECH AI        EXPRESSION AI
          |                |                |
          +----------------+----------------+
                           |
                           v
                STRUCTURED MODEL OUTPUTS
                           |
                           v
                ADAPTIVE MULTIMODAL FUSION
                           |
                +----------+----------+
                |                     |
                v                     v
        MISSING MODALITY       UNCERTAINTY
           HANDLING            ESTIMATION
                |                     |
                +----------+----------+
                           |
                           v
                CROSS-MODAL DISAGREEMENT
                       DETECTION
                           |
                           v
                  EXPLAINABLE AI LAYER
                           |
                           v
                    FINAL RESULTS
                           |
                           v
                CONVERSATIONAL RESPONSE
                           |
                           v
                     REACT UI
```

---

## 3. Main System Components

### 3.1 Frontend Layer

**Technology:** React

Responsibilities:

- Accept text input.
- Upload audio files.
- Capture microphone input with user permission.
- Upload images and access webcam with user permission.
- Display individual modality predictions.
- Display combined multimodal predictions.
- Show uncertainty and disagreement indicators.
- Present explanations and processing status.

### 3.2 Backend Layer

**Technology:** Python and FastAPI

Responsibilities:

- Receive frontend requests.
- Validate and preprocess incoming data.
- Identify available input modalities.
- Route inputs to the relevant AI modules.
- Coordinate model inference.
- Handle asynchronous processing where required.
- Connect model outputs to the fusion and explanation components.
- Return structured results to the frontend.

The backend will act as the central orchestration layer for the application.

### 3.3 Input Validation and Quality Assessment

Responsibilities:

- Validate input formats and file sizes.
- Identify missing or invalid inputs.
- Assess audio quality using relevant signal characteristics.
- Assess visual quality using factors such as blur, lighting and face visibility.
- Check text input validity and preprocessing requirements.
- Generate input-quality information for downstream processing.

Input quality and model uncertainty will be treated as related but distinct concepts.

For example, poor audio quality may affect model reliability, while predictive uncertainty represents uncertainty in the model's output.

### 3.4 Text Intelligence Module

**Candidate technologies:** Hugging Face Transformers, MuRIL and XLM-RoBERTa.

Workflow:

Text Input → Language and Text Preprocessing → Tokenisation → Model Inference → Classification Output.

Responsibilities:

- Process Hindi, English and Hinglish text.
- Handle Roman-script Hindi and code-mixed expressions.
- Perform sentiment classification.
- Perform emotion-related classification.
- Generate class probabilities.
- Provide suitable text feature explanations.

Potential research directions:

- Multilingual transfer learning.
- Multitask sentiment and emotion classification.
- Handling spelling variations and informal expressions.
- Evaluation on code-mixed datasets.

### 3.5 Audio Intelligence Module

**Candidate technologies:** Librosa, Whisper and Wav2Vec2/SpeechBrain.

Workflow:

Audio Input → Audio Preprocessing → Speech Transcription and Acoustic Feature Extraction → Independent Classification Tasks → Structured Output.

Responsibilities:

- Convert speech into text using automatic speech recognition.
- Analyse acoustic characteristics independently of transcription.
- Perform speech emotion-related classification.
- Estimate relevant audio-quality information.
- Generate model confidence and uncertainty information.

Speech transcription and acoustic classification will remain separate tasks.

A transcription result will not automatically be treated as an acoustic emotion prediction.

### 3.6 Vision Intelligence Module

**Candidate technologies:** OpenCV, MediaPipe and CNN/Vision Transformer models.

Workflow:

Image/Video Input → Frame Selection → Face Detection → Visual Preprocessing → Expression Classification → Structured Output.

Responsibilities:

- Detect faces in images and video frames.
- Extract suitable facial landmarks and visual features.
- Analyse visible facial-expression patterns.
- Generate expression-related classifications.
- Estimate visual input quality.
- Provide model confidence and uncertainty information.

The system will describe visible facial-expression patterns rather than claiming to identify a person's actual internal emotional state.

### 3.7 Adaptive Multimodal Fusion Module

**Technology:** PyTorch.

Responsibilities:

- Receive structured outputs from individual AI modules.
- Identify available modalities.
- Consider modality-level input quality.
- Consider calibrated uncertainty estimates.
- Learn the contribution of available modalities.
- Combine predictions using an adaptive fusion mechanism.
- Handle incomplete or missing modality combinations.

Development approach:

1. Establish individual unimodal baselines.
2. Implement a conventional late-fusion baseline.
3. Develop reliability-aware adaptive fusion.
4. Investigate advanced uncertainty-aware fusion techniques.

The system will not assume that all three modalities are always available.

### 3.8 Missing-Modality Handling

Responsibilities:

- Identify which modalities are unavailable.
- Support text-only, audio-only and vision-only inference.
- Support available combinations of two modalities.
- Avoid requiring missing inputs for inference.
- Investigate representation generation and prompt-based missing-modality techniques as advanced experiments.

The initial implementation will use available-modality fusion. More advanced missing-representation generation can be investigated after establishing a baseline.

### 3.9 Uncertainty Estimation and Calibration

Responsibilities:

- Estimate modality-wise prediction uncertainty.
- Investigate calibration techniques.
- Compare uncertainty across available modalities.
- Communicate uncertainty in the final output.
- Avoid presenting every prediction as equally reliable.

Potential techniques include calibrated probability estimates and uncertainty-aware latent representations.

Calibration and uncertainty estimation will be evaluated using appropriate metrics such as Expected Calibration Error and Brier Score.

### 3.10 Cross-Modal Disagreement Detection

Responsibilities:

- Compare predictions from available modalities.
- Identify significant differences between modality outputs.
- Generate disagreement indicators.
- Communicate conflicting predictions.
- Preserve uncertainty when modalities provide inconsistent information.

Disagreement will not be interpreted as evidence of deception or hidden emotions.

### 3.11 Explainable AI Module

**Candidate techniques:**

- SHAP/LIME for suitable text models.
- Audio feature attribution and acoustic analysis.
- Grad-CAM for suitable vision models.
- Modality contribution analysis for fusion.

Responsibilities:

- Explain influential input features.
- Display modality-level contributions.
- Explain why certain inputs may have limited influence.
- Communicate prediction limitations.
- Present understandable explanations to users.

Explanation techniques will be selected according to the model architecture and task.

### 3.12 Conversational Response Layer

Responsibilities:

- Convert structured model outputs into understandable responses.
- Explain individual and combined predictions.
- Communicate uncertainty and modality disagreement.
- Explain relevant limitations.
- Optionally generate speech using text-to-speech.

The conversational response layer will remain separate from the classification models.

### 3.13 Database Layer

**Technology:** PostgreSQL.

Potential data:

- User account information.
- User consent records.
- Analysis metadata.
- Optional analysis history.
- Model and prediction metadata where appropriate.

Raw audio and video will not be stored by default.

Any optional history or data retention will require suitable user consent and privacy controls.

---

## 4. Structured Model Output

Each AI module will return a consistent structured output.

Potential fields:

- Modality name.
- Processing status.
- Predicted class labels.
- Class probabilities.
- Confidence or uncertainty estimates.
- Input-quality information.
- Relevant explanation metadata.

A simplified conceptual example:

```json
{
  "modality": "audio",
  "status": "success",
  "prediction": "sadness_related_signal",
  "probabilities": {
    "sadness": 0.72,
    "neutral": 0.18,
    "anger": 0.10
  },
  "quality": "good",
  "uncertainty": null
}
```

The example is illustrative. Actual model outputs, labels and uncertainty fields will depend on the selected models and calibration methods.

---

## 5. Data Flow

1. User provides one or more supported input modalities.
2. React sends the input to the FastAPI backend.
3. Backend validates input formats and identifies available modalities.
4. Input-quality assessment evaluates relevant quality characteristics.
5. Backend routes each available input to its corresponding AI module.
6. Individual models generate structured predictions.
7. Fusion module combines available modality outputs.
8. Missing-modality handling supports incomplete input combinations.
9. Uncertainty estimation evaluates prediction reliability.
10. Disagreement detection identifies conflicting modality outputs.
11. Explainability module prepares supporting information.
12. Backend returns structured results to the frontend.
13. Conversational response layer explains the results in understandable language.

---

## 6. Real-Time Architecture

The real-time system will investigate:

- Browser-based microphone access.
- Browser-based webcam access.
- Short audio processing windows.
- Selected video-frame processing.
- Streaming updates using WebSockets where required.
- Asynchronous inference.
- Conversational responses.
- Model optimisation for latency.

Real-time performance will depend on model size, hardware, network conditions and processing requirements.

---

## 7. Deployment Architecture

**Candidate technologies:** Docker and suitable hosting services.

Responsibilities:

- Package the frontend and backend.
- Organise AI model components for reproducible execution.
- Manage model dependencies and configuration.
- Support API integration.
- Prepare application deployment.
- Maintain environment-specific settings.

The deployment architecture will be refined after the individual modules and backend integration are implemented.

---

## 8. Evaluation and Monitoring

The system will be evaluated at both individual-module and integrated-system levels.

Potential evaluation areas:

- Classification performance.
- Macro-F1 and per-class performance.
- Prediction calibration.
- Missing-modality robustness.
- Noise robustness.
- Cross-modal disagreement behaviour.
- Fusion performance.
- Inference latency.

Experiments will compare unimodal baselines, conventional fusion and adaptive fusion under comparable evaluation conditions.

---

## 9. Architecture Design Principles

- Modular development.
- Independent model inference.
- Reusable APIs.
- Structured model outputs.
- Available-modality support.
- Reliability-aware predictions.
- Calibrated uncertainty.
- Explainability and transparency.
- Privacy and responsible data handling.
- Reproducible evaluation and deployment.

---

## 10. Future Improvements

- Additional Indian language support.
- Improved code-mixed NLP models.
- Advanced multimodal fusion architectures.
- Representation generation for missing modalities.
- Improved low-resource language handling.
- Optimised real-time inference.
- Larger and more diverse evaluation datasets.
- Further calibration and robustness experiments.

---

## 11. Conclusion

BharatNLP will follow a modular end-to-end architecture integrating multilingual NLP, speech analysis and computer vision into a unified multimodal application.

Its proposed adaptive fusion, missing-modality handling, uncertainty estimation, disagreement detection and explainability components aim to improve the transparency and reliability of multimodal predictions.

The architecture will be implemented incrementally, beginning with independent unimodal baselines and progressing towards an integrated application. The effectiveness of the proposed methods will be established through systematic experiments and evaluation.

The system will analyse observable language, acoustic and facial-expression patterns rather than claiming to identify a person's true internal emotional state.
