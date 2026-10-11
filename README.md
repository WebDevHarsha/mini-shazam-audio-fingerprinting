# Mini Shazam: Audio Fingerprinting

A Python implementation of a Shazam-inspired audio recognition system using spectrogram analysis, spectral landmarks, audio fingerprints, and time-offset matching.

The project explores how a short audio clip can be matched against a music library without comparing the raw audio waveforms directly.

## Overview

Music recognition systems need to identify a song even when the query is only a short segment of the original recording. This project implements a simplified audio-fingerprinting pipeline inspired by the research paper *An Industrial-Strength Audio Search Algorithm* by Avery Li-Chun Wang.

The system extracts distinctive features from audio, converts them into compact fingerprints, indexes those fingerprints, and identifies matching tracks using time-offset voting.

## How It Works

1. **Audio preprocessing:** Load audio files and convert them into a suitable numerical representation.
2. **Spectrogram generation:** Apply the Short-Time Fourier Transform (STFT) to analyze frequency content over time.
3. **Landmark detection:** Identify prominent local peaks in the spectrogram.
4. **Fingerprint generation:** Pair spectral peaks and encode their frequency and time relationships into hashes.
5. **Indexing:** Store fingerprints in an in-memory index associated with their track and time positions.
6. **Query matching:** Extract fingerprints from a query clip and look for matching hashes in the index.
7. **Time-offset voting:** Determine which track has the strongest agreement in relative time offsets.

## Project Structure

```text
mini-shazam-audio-fingerprinting/
├── README.md
├── audio_fingerprinting_from_paper.ipynb
├── requirements.txt
├── .gitignore
└── sample_track.wav
```

## Technologies Used

- Python
- NumPy
- SciPy
- Matplotlib
- SoundFile
- Jupyter Notebook / Google Colab

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/mini-shazam-audio-fingerprinting.git
cd mini-shazam-audio-fingerprinting
```

Replace `YOUR_USERNAME` with your GitHub username.

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Prepare the music library

Create a directory named `music_library` and place your audio files inside it.

```text
music_library/
├── song_01.wav
├── song_02.wav
└── song_03.wav
```

The notebook should be configured to read audio files from this directory. In Google Colab, the directory can be created under `/content/music_library`.

### 4. Run the notebook

Open `audio_fingerprinting_from_paper.ipynb` in Jupyter Notebook or upload it to Google Colab. Run the cells in order to build the fingerprint index and test a query clip.

## Sample Audio Attribution

The sample audio used for testing is:

- **Track:** Я не увижу сказки ветра (RUS)
- **Artist:** Andrey Petrov
- **Source:** Free Music Archive
- **License:** Creative Commons Attribution (CC BY)

The track is included for audio-fingerprinting experiments. Attribution is provided to the original artist and source.

**Original track:** Add the direct Free Music Archive track URL here.

## Research Reference

Wang, Avery Li-Chun. “An Industrial-Strength Audio Search Algorithm.” Proceedings of the International Conference on Music Information Retrieval (ISMIR), 2003.

The implementation is inspired by the paper's approach to spectral peaks, landmark-based fingerprints, and time-offset matching.

**Paper:** https://www.ee.columbia.edu/~dpwe/papers/Wang03-shazam.pdf

## Limitations

- This is an educational prototype, not a production-scale music recognition service.
- Matching quality depends on landmark selection, fingerprint parameters, audio quality, and the size of the indexed library.
- The fingerprint index is stored in memory and is not persistent across runtime restarts.
- The system has not been benchmarked against a large-scale commercial music database.

## Future Improvements

- Persist fingerprints in a database.
- Improve matching robustness under background noise and audio transformations.
- Evaluate accuracy across different query lengths and recording conditions.
- Build a web interface for uploading audio clips and displaying match results.

## License

The project's source code is intended for educational and research purposes. The sample audio is subject to its own attribution and licensing requirements. Refer to the original track page for the applicable terms.
