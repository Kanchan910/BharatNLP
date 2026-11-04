# BharatNLP – System Architecture

## 1. Introduction

BharatNLP follows a modular multimodal AI architecture that integrates Natural Language Processing, Speech Emotion Recognition and Computer Vision.

The system is designed to process text, audio and visual inputs independently or together, combine available model outputs through adaptive multimodal fusion and present explainable, uncertainty-aware predictions.

## 2. High-Level Architecture

```text
                    USER
                     |
                     v
             REACT FRONTEND
                     |
          +----------+----------+
          |          |          |
          v          v          v
       TEXT       AUDIO       IMAGE/
       INPUT      INPUT       VIDEO
          |          |          |
          +----------+----------+
                     |
                     v
              FASTAPI BACKEND
                     |
          +----------+----------+
          |          |          |
          v          v          v
       TEXT NLP   AUDIO AI   VISION AI
          |          |          |
          v          v          v
       TEXT       SPEECH     EXPRESSION
       OUTPUT     OUTPUT      OUTPUT
          |          |          |
          +----------+----------+
                     |
                     v
          ADAPTIVE MULTIMODAL
                  FUSION
                     |
                     v
          DISAGREEMENT DETECTION
                     |
                     v
           EXPLAINABLE AI AND
                UNCERTAINTY
                     |
                     v
              FINAL RESULTS
                     |
                     v
          CONVERSATIONAL RESPONSE
```

## 3. Main System Components

### 3.1 Frontend Layer

Technology: React

Responsibilities:
- Accept text input.
- Upload audio files.
- Capture microphone input.
- Upload images and access webcam with permission.
- Display individual and combined predictions.
- Show explanations and uncertainty indicators.

### 3.2 Backend Layer

Technology: Python and FastAPI

Responsibilities:
- Receive frontend requests.
- Validate input data.
- Route inputs to appropriate AI modules.
- Coordinate model inference.
- Connect the fusion and explanation components.
- Return structured results.

### 3.3 Text Intelligence Module

Candidate technologies: Hugging Face Transformers, MuRIL and XLM-RoBERTa.

Workflow:

Text Input → Preprocessing → Tokenisation → Model Inference → Classification Output.

Expected outputs:
- Sentiment classification.
- Emotion-related classification.
- Class probabilities.
- Text feature attribution.

### 3.4 Audio Intelligence Module

Candidate technologies: Librosa, Whisper and Wav2Vec2/SpeechBrain.

Workflow:

Audio Input → Audio Preprocessing → Speech Transcription and Acoustic Feature Extraction → Audio Classification → Output.

Expected outputs:
- Speech transcript.
- Acoustic classification.
- Model confidence.
- Audio quality information.

Speech transcription and acoustic classification will be implemented as separate tasks.

### 3.5 Vision Intelligence Module

Candidate technologies: OpenCV, MediaPipe and CNN/Vision Transformer models.

Workflow:

Image/Video Input → Face Detection → Image Preprocessing → Expression Classification → Output.

Expected outputs:
- Face detection information.
- Visible facial-expression classification.
- Model confidence.
- Visual quality information.

### 3.6 Adaptive Multimodal Fusion Module

Technology: PyTorch.

Responsibilities:
- Receive individual modality outputs.
- Consider modality availability and quality.
- Learn the contribution of each available modality.
- Combine available model predictions.
- Handle missing or noisy inputs.

A baseline fusion model will be developed before implementing adaptive fusion.

### 3.7 Disagreement Detection

Responsibilities:
- Compare predictions from available modalities.
- Identify significant differences.
- Generate disagreement indicators.
- Communicate uncertain or conflicting outputs.

The system will not interpret disagreement as evidence of deception or hidden emotions.

### 3.8 Explainable AI Module

Candidate techniques:
- SHAP/LIME for suitable text models.
- Audio feature analysis.
- Grad-CAM for suitable vision models.
- Modality contribution analysis.

Responsibilities:
- Explain influential input features.
- Display modality-level contributions.
- Communicate prediction limitations.

### 3.9 Conversational Response Layer

Responsibilities:
- Convert structured model outputs into understandable responses.
- Explain individual and combined predictions.
- Communicate uncertainty and limitations.
- Optionally provide speech output using text-to-speech.

The response layer will be separate from the classification models.

## 4. Data Flow

1. User provides one or more input modalities.
2. React sends validated requests to the FastAPI backend.
3. Backend routes inputs to the relevant AI services.
4. Individual models generate structured predictions.
5. Fusion module combines available predictions.
6. Disagreement detection and uncertainty estimation evaluate the results.
7. Explainability module prepares supporting information.
8. The backend returns results to the frontend.
9. The conversational response layer can explain the results.

## 5. Database Layer

Technology: PostgreSQL.

Potential data:
- User account information.
- Consent records.
- Analysis metadata.
- Optional analysis history.

Raw audio and video will not be stored by default.

## 6. Real-Time Architecture

The real-time system will support:
- Browser-based microphone access.
- Browser-based webcam access.
- Short audio processing windows.
- Selected video-frame processing.
- Streaming updates using WebSockets where required.
- Conversational responses.

Real-time performance will depend on model size, hardware and network conditions.

## 7. Deployment Architecture

The application will be prepared for deployment using Docker and suitable hosting services.

The frontend, backend and AI model components will be organised to support reproducible deployment and maintenance.

## 8. Architecture Design Principles

- Modular development.
- Independent model services.
- Reusable APIs.
- Scalable integration.
- Reliability-aware predictions.
- Explainability and uncertainty.
- Privacy and responsible data handling.

## 9. Future Improvements

- Additional Indian language support.
- Improved multimodal model architectures.
- Better low-resource language handling.
- Model optimisation for real-time inference.
- Expanded evaluation datasets.

## 10. Conclusion

BharatNLP will follow a modular end-to-end architecture that combines multilingual NLP, audio intelligence and computer vision into a unified multimodal application.

Its adaptive fusion, disagreement detection and explainability components aim to make the platform more transparent and reliability-aware.