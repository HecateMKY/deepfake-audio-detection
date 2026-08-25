Deepfake Audio Detection

CNN-BiLSTM deepfake audio detector — 98.27% accuracy on a 13,500+ sample held-out test set.

Final year dissertation (University of Exeter, ECM3401): a binary audio classifier that distinguishes authentic human speech from AI-generated ("deepfake") speech, built to support anti-phishing / voice-fraud detection use cases.

Overview

The system performs binary classification of audio as:

REAL — genuine human speech
FAKE — AI-generated / synthetic speech

The final pipeline uses:

log-Mel spectrogram feature extraction and normalisation
a CNN + BiLSTM classifier
a prototype inference function with ~50ms per-file processing time
Dataset

A 480,000+ sample multi-source labelled audio dataset was constructed and balanced from:

Real speech: LJSpeech, Mozilla Common Voice, VCTK
Synthetic speech: WaveFake, ASVspoof2019, Kokoro-82M (generated in-house — see SoundTransfer.ipynb)

Using multiple real and synthetic sources — rather than a single generator — helps the model generalise beyond any one synthesis method, and the dissertation report critically evaluates how well it generalises to unseen synthesis tools.

All external datasets are credited to their original authors; use of each is subject to its own licence — see the individual dataset sources for terms.

Repository contents
File	Purpose
deepfake_audio_detection.ipynb	Main notebook — feature extraction, model training, and evaluation
SoundTransfer.ipynb	Generates additional synthetic ("FAKE") speech samples using Kokoro-82M, used to enrich the training dataset
GraphGenerator.ipynb	Produces the result plots and reliability/evaluation charts used in the report
Final_Report.pdf	Full dissertation report (methodology, results, evaluation, limitations)
Results
98.27% accuracy on a 13,500+ sample held-out test set
~50ms per-file inference time in the prototype pipeline
Requirements
Python 3.10+
TensorFlow 2.21.0
librosa, numpy, scikit-learn, matplotlib
bash
pip install -r requirements.txt
Running
Organise audio files into real/ and fake/ directories
Run deepfake_audio_detection.ipynb to extract features, train, and evaluate the model
(Optional) Run SoundTransfer.ipynb first if you want to regenerate the Kokoro-82M synthetic samples
Run GraphGenerator.ipynb to reproduce the result plots
Author

Ma Ka Yu — BSc (Hons) Computing, University of Exeter
