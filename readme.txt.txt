# Deepfake Audio Detection

## Overview

This ZIP contains the **Data / Code / Logbook** submission for an audio deepfake detection project.

The system performs **binary classification** of audio as:

- **REAL**
- **FAKE**

The final pipeline uses:

- **log-Mel spectrogram features**
- a **CNN + BiLSTM** classifier
- a saved trained model: `deepfake_detector.keras`
- saved training normalisation statistics: `norm_stats.npy`

### Short dataset summary

The dataset combines multiple **real speech corpora** and multiple **synthetic / spoofed speech sources** so that the classifier is not trained on only one fake generator family.

How to run
- Install Python 3.10 and the packages in requirements.txt
- Put the dataset in dataset/audio/
- Put real audio in dataset/audio/real/ and fake audio in dataset/audio/fake/
- For training, run python src/<TRAIN_SCRIPT>.py and set DATASET_ROOT = "dataset/audio"
- Save or keep deepfake_detector.keras and norm_stats.npy in the project root after training
- For single-file inference, run python src/<INFERENCE_SCRIPT>.py --input <AUDIO_FILE> and load deepfake_detector.keras with norm_stats.npy

Dataset tree
- dataset/
  - audio/
    - real/ 
      - LJSpeech/       
            - VCTK/ 
      - CommonVoice/ 
    - fake/ 
      - ASVspoof2019_LA_train/ 
      - ASVspoof2019_LA_dev/
      - ASVspoof2019_LA_eval/
      - ljspeech_hifiGAN/ 
      - ljspeech_waveglow/ 
      - ljspeech_melgan/ 
      - ljspeech_parallel_wavegan/ 
      - Kokoro-82M/ 

Requirements
# Python 3.12
tensorflow==2.21.0
librosa==0.11.0
soundfile==0.13.1
scikit-learn==1.5.2
matplotlib==3.10.8
pandas==2.3.3
openpyxl==3.1.5

Citation & Attribution

This project uses external datasets for academic research purposes.
All datasets remain under their original licences.

Please cite the following sources where applicable:

WaveFake Dataset – Deepfake audio detection dataset (WaveFake)
ASVspoof 2019 – Automatic Speaker Verification Spoofing and Countermeasures Challenge
VCTK Corpus – English multi-speaker speech dataset
Mozilla Common Voice – Open-source multilingual speech dataset
LJSpeech Dataset – Single-speaker English speech dataset
Licence Notice

External datasets are not owned by this project and are subject to their respective licences and terms of use.
If redistributing any dataset files, users must comply with the original dataset licences.
