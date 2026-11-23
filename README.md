# Multi-Modal Vocalization Segmentation & Autonomic Heart-Rate Alignment

An open-source, two-stage Python pipeline for automated syllable segmentation, fundamental frequency ($F_0$) extraction, and event-locked alignment with continuous autonomic heart-rate (BPM) signals.

### Stage 1: Acoustic Segmentation & Pitch ($F_0$) Tracking
**Interactive Notebook:** [Open Stage 1 Notebook](notebooks/vocalization_acoustics_replication.ipynb)

![Vocalization Analysis Summary](vocal_bout_analysis.png)

### Stage 2: Event-Locked Autonomic Heart-Rate Alignment
**Interactive Notebook:** [Open Stage 2 Notebook](notebooks/02_multimodal_hr_alignment.ipynb)

![Multimodal Heart Rate Alignment](multimodal_hr_alignment.png)

## Pipeline Architecture
1. **Stage 1 — Automated Acoustic Feature Extraction (`librosa`):** Generates synthetic multi-syllable vocal bouts, segments vocal onsets/offsets via RMS energy thresholding (`top_db=25`, $>80\text{ ms}$ duration filter), tracks $F_0$ via probabilistic YIN (`librosa.pyin`), and computes inter-syllable intervals (ISIs).
2. **Stage 2 — Event-Locked Physiological Alignment (`numpy`, `pandas`):** Uses vocalization onset timestamps (`onset_sec`) as $t = 0$ event triggers to epoch (`[-2.0s, +3.0s]`) and baseline-correct continuous 10 Hz autonomic heart-rate trajectories across vocal bouts.

## How to Run
Click either **Open Notebook** link above to view the rendered code and plots on GitHub, then click the **Open in Colab** button at the top of the notebook to execute the pipeline in your browser.
