![Japanese_20](https://i.imgur.com/8jb2hrr.png)
<!-- ![Japanese_20](https://github.com/user-attachments/assets/d7234b0f-c7a5-4c5d-ab05-b10a5c88ce8a) -->

🔴 Phonemer is currently private. Please contact me if interested.

# Phonemer

Phonemer is a tool designed for grapheme and syllable detection and positioning in several languages (and multilingual), developed for a friend's new piece; [Georges Bloch](https://www.ircam.fr/dashboard/georges-bloch/). It detects phonemes or syllables and saves them into a CUE file, [Max](https://cycling74.com) coll file, or as markers in an audio file.

Olivier Pasquet _2025

## Features
- **Grapheme and Syllable Detection**: Accurately detects graphemes and syllables in audio files.
- **Multiple Output Formats**: Saves results in CUE files, [Max](https://cycling74.com) coll files, or as markers in WAV audio files.
- **GPU Support**: Runs on GPU by default for enhanced performance.
- **Automatic Model Download**: Automatically downloads the necessary transformer models from [HuggingFace](https://huggingface.co) for each language. It mostly uses facebook/wav2vec2-large-960h, jonatasgrosman/wav2vec2-large-xlsr-53-XXX and alibaba-pai/wav2vec2-large-XXX.

## Dependencies
Phonemer requires Python 3.13.5 and has been tested on both macOS and Windows. Other versions have not been tested.
Phonemer utilizes [Facebook Fairseq's wav2vec](https://github.com/facebookresearch/fairseq/tree/main/examples/wav2vec) for grapheme detection and the `wavfile_OP` provided in this distribution or on its own repository here.

Below are the required Python packages:<br>
numpy - 2.3.2<br>
torch- 2.7.1<br>
torchaudio - 2.7.1<br>
tqdm - 4.67.1<br>
transformers- 4.54.1<br>
safetensors - 0.5.3<br>
pyphen - 0.17.2<br>
syllables - 1.1.1<br>
tokenizers - 0.21.4<br>
huggingface-hub - 0.34.3

## Installation

To install Phonemer, follow these simple basic steps:

1. Move to the directory where `phonemer.py` is located
2. Create a virtual environment:<br>
    `python3 -m venv Phonemer_venv`
OR<br>
   `python -m venv Phonemer_venv`

3. Activate the virtual environment:<br>
   `source Phonemer_venv/bin/activate`
4. Upgrade pip and install the required packages:<br>
   `pip install --upgrade pip`<br>
   `pip install torch torchaudio transformers pyphen syllables soundfile`

4. Deactivate the virtual environment after use:<br>
`deactivate`

## Usage Examples

- Activate the virtual environment, then...

- Spoken Words in French:<br>
`python phonemer.py --input André_Malraux_bio.wav --language French_1`

- Spoken Words in English:<br>
`python phonemer.py --input George_Orwell.wav --language English_1 --show_vocab --syllables --save_markers --save_coll --save_cue --time_shift -86`

- Sung Words in English:<br>
`python phonemer.py --input Lady_Gaga_Shallow.wav --language English_1 --save_markers --time_shift -72`

- Deactivate the virtual environment.

## Outputs

The system generates potential grapheme or syllable outputs, displaying each result with its name and corresponding confidence probability (calculated as the mean of grapheme probabilities for syllables).

`--save_cue`: save as CUE format file
```python
    TRACK 01 AUDIO
	TITLE "ATTTHEAPPE 0.9993300437927246"
	INDEX 01 00:00:00
  TRACK 02 AUDIO
	TITLE "EXXOFT 0.9712339282035828"
	INDEX 01 00:00:44
...
```
`--save_coll`: save as coll text format file
```python
0, ATTTHEAPPE 0.9993300437927246;
594, EXXOFT 0.9712339282035828;
1314, THEP 0.9999649922053019;
1474, PYRRAM 0.9438934922218323;
1733, MID 0.9999908208847046;
...
```
`--save_markers`: save markers in WAV audio file

<!-- <img width="400" height="330" alt="Screenshot 2025-08-06 at 16 24 43" src="https://github.com/user-attachments/assets/83b503e1-25ad-4d42-8375-20de2ca9870f" /> -->
<img width="400" height="330" alt="Screenshot 2025-08-06 at 16 24 43" src="https://i.imgur.com/z2cmGYa.png" />

## Command-Line Arguments

| Argument                | Type        | Default      | Description                                                  |
|-------------------------|-------------|--------------|--------------------------------------------------------------|
| `-i` or `--input`      | Required    | —            | Path to the input audio file                                 |
| `--syllables`          | Optional    | False        | Outputs syllables; otherwise, outputs graphemes              |
| `--language`           | Optional    | French_1     | Language used                                               |
| `--threshold`          | Optional    | 0.3          | Threshold beyond which probability grapheme is kept         |
| `--save_cue`           | Optional    | True         | Save CUE file                                              |
| `--save_markers`       | Optional    | False        | Save markers in WAV audio file; channel number etc. are kept|
| `--save_coll`          | Optional    | False        | Save coll file for Max                                      |
| `--show_vocab`         | Optional    | False        | Show vocab dictionary of the used model                     |
| `--time_shift`         | Optional    | 0            | Adjust possible positive or negative latencies in ms        |

## Available Languages

See in `phonemer.py` for the model's names and URLs.
French_1, French_2, English_1, English_2, German, Spanish, Italian, Portuguese, Russian, Dutch, Polish, Chinese_1, Chinese_2, Finnish, Japanese_1, Japanese_2, Greek, Arabic, Persian, Hebrew, Hungarian, Multilingual_1, Multilingual_2

## Usage restrictions:
This code cannot be used for any of [Ircam](https://www.ircam.fr) productions.
