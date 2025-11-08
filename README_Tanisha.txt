MFA Alignment Assignment - Tanisha Teware
Date: [11/7/2025]

Step 1: Installation of Montreal Forced Aligner (MFA)

Install Miniconda from
🔗 https://docs.conda.io/en/latest/miniconda.html

Open Anaconda Prompt and create a new environment:
conda create -n aligner -c conda-forge montreal-forced-aligner

Activate the environment:
conda activate aligner

Verify installation:
mfa version

Step 2: Dataset Preparation

Create a project folder, for example:
C:\Users\VICTUS\data\

Inside data, create two folders:
wav/      → for .wav audio files
lab/      → for text transcript files
Ensure every .wav file has a matching .txt file with the same name.

✅ Example:
F2BJRLP1.wav
F2BJRLP1.txt

Step 3: Convert Audio (if needed)
If your .wav files are not 16kHz mono, convert them using ffmpeg:
mkdir "C:\Users\VICTUS\data\converted"
for %f in ("C:\Users\VICTUS\data\wav\*.wav") do ffmpeg -i "%f" -ac 1 -ar 16000 "C:\Users\VICTUS\data\converted\%~nf.wav"

Step 4: Run MFA Alignment
Run the following command in your Anaconda Prompt:
mfa align "C:\Users\VICTUS\data\converted" english_us_arpa english_mfa "C:\Users\VICTUS\alignment_output" --clean

This command:
Aligns your .wav and .txt pairs

Uses the English US ARPA dictionary and English MFA acoustic model

Outputs alignment .TextGrid files to alignment_output

Step 5: Validate the Corpus (optional)

To check the corpus setup before alignment:
mfa validate "C:\Users\VICTUS\data\converted" english_us_arpa english_mfa

Step 6: View Alignments in Praat

Install Praat
Open a .wav and its corresponding .TextGrid file from the alignment_output folder.

Observe word and phoneme boundaries aligned automatically.

Step 7: Outputs

All aligned .TextGrid files are in:
C:\Users\VICTUS\alignment_output

These files can be visualized or analyzed for timing and segmentation accuracy.

Report Summary

Dictionary used: english_us_arpa
Acoustic model: english_mfa
Corpus: 6 utterances from ISLE/F2BJRLP dataset

Observations: MFA successfully aligned audio and transcript pairs with clear word/phone boundaries.

🧩 Repository Contents
Tanisha_MFA_Assignment/
│
├── data/
│   ├── wav/
│   └── lab/
│
├── alignment_output/
│   ├── *.TextGrid
│
├── README.md
└── Tanisha_MFA_Report.pdf

Submission

GitHub Repo: https://github.com/tanisha554-ui/Tanisha_MFA_Assignment

Report (PDF): https://drive.google.com/file/d/1So3uyaXUS5785Zn-GCtOvl_nSVmF--9f/view?usp=sharing
