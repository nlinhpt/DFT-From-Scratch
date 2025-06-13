# DFT-From-Scratch
The Discrete Fourier Transform (DFT) is a fundamental mathematical tool in digital signal processing that transforms a finite sequence of discrete time-domain samples into their corresponding frequency-domain representation. By decomposing a signal into its constituent sinusoidal components, the DFT reveals how much of each frequency is present in the original signal.

Unlike the continuous Fourier Transform, which operates on continuous signals, the DFT is designed for numerical computation and is well-suited to digital systems. Given its discrete nature, the DFT is especially useful in applications involving audio processing, image analysis, telecommunications, and more.

In this project, we implement the DFT using Python to gain a deeper understanding of its inner workings. We then apply it to a practical task: reducing noise in audio signals. By analyzing the frequency components of a noisy signal, we can identify and attenuate the undesired frequencies, thereby improving the overall audio quality.

# 🎧 Noise Reduction with Discrete Fourier Transform (DFT)

## 📌 Introduction

In real-world signals such as audio, image, or sensor data, the presence of **noise** often hides the meaningful components. For instance, background white noise can obscure important frequencies in an audio recording. To recover clean information, we need to transform the signal from the **time domain** to the **frequency domain** using the **Discrete Fourier Transform (DFT)**.

This project demonstrates how to apply DFT and its fast implementation (FFT) to analyze and denoise audio signals.

---

## 🧮 Mathematical Background

### ⚙️ 1. Roots of Unity

DFT uses complex roots of unity:

\[
\omega = e^{-2\pi i / n}
\]

These roots form the basis of the transformation and are arranged in the **Fourier matrix**.

---

### ⚙️ 2. Fourier Matrix \( F_n \)

An \( n \times n \) matrix defined as:

\[
(F_n)_{jk} = \omega^{jk}
\]

**Properties**:
- Orthogonality: columns are perpendicular.
- Equal norm: all columns have norm \( \sqrt{n} \).
- A special case of the **Vandermonde matrix**.

---

### ⚙️ 3. DFT and Inverse DFT

- **DFT**:
  \[
  X = F_n \cdot x
  \]

- **IDFT** (Inverse DFT):
  \[
  x = \frac{1}{n} F_n^* \cdot X
  \]

Where:
- \( x \): signal in time domain
- \( X \): signal in frequency domain

---

## 🛠️ Signal Denoising Pipeline

### 🔎 Step 1: Load and Analyze Audio

Use libraries such as `scipy.io.wavfile` or `librosa` to:
- Load the audio file
- Inspect sample rate, channels (mono/stereo), duration

### 📊 Step 2: Visualize

- Plot the waveform in the time domain
- Apply **FFT** to convert signal to frequency domain
- Plot the frequency spectrum to identify noise

### 🔧 Step 3: Noise Reduction Techniques

- **Spectral Filtering**:
  - Suppress noisy frequencies by setting their amplitude to zero or reducing them

- **Apply Filter Types**:
  - Low-pass, High-pass, Band-pass filters depending on desired frequency ranges

- **Automatic Noise Reduction**:
  - Use libraries such as `noisereduce` or `pyroomacoustics`

- **Fixed Noise Removal**:
  - Subtract noise profile (e.g., power-line hum) if known

### 🎛️ Step 4: Clean Signal Processing

- **Smoothing**: Use Gaussian or median filters to remove random noise
- **Synchronization**: Align phase or time shifts if needed
- **Normalization**: Keep amplitudes within valid range (avoid clipping/distortion)

### 🔁 Step 5: Output and Validation

- **Listen to Result**: Compare before and after
- **Plot Cleaned Spectrum**
- **Save Output**: Write processed audio to `.wav`

---

## 🧪 Tools Used

- `numpy` — core FFT and array processing
- `scipy.io.wavfile` / `librosa` — audio I/O and analysis
- `matplotlib` — visualization
- `noisereduce` — optional auto denoising
- 🧰 Optional: MATLAB, Audacity, Adobe Audition

---

## 📈 Optimization

- Tune:
  - Thresholds for frequency removal
  - Filter cutoffs (low/high-pass)
- Repeat:
  - Additional smoothing/filtering
  - Multi-stage denoising if needed

---

## 📂 Folder Structure

```bash
.
├── audio/
│   ├── noisy_sample.wav
│   └── clean_output.wav
├── notebooks/
│   └── denoise_fft_demo.ipynb
├── README.md
└── requirements.txt

