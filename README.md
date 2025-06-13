# 🎧 Noise Reduction with Discrete Fourier Transform (DFT)

## 📌 Introduction

In real-world signals such as audio, image, or sensor data, the presence of **noise** often hides the meaningful components. For instance, background white noise can obscure important frequencies in an audio recording. To recover clean information, we need to transform the signal from the **time domain** to the **frequency domain** using the **Discrete Fourier Transform (DFT)**.

This project demonstrates how to apply DFT and its fast implementation (FFT) to analyze and denoise audio signals.

---

## 🧮 Mathematical Background

### ⚙️ 1. Roots of Unity

DFT uses complex roots of unity, which are complex numbers of the form:

$$
\omega = e^{2\pi i / n} = \cos\left(\frac{2\pi}{n}\right) + i \sin\left(\frac{2\pi}{n}\right)
$$

These numbers $\{1, \omega, \omega^2, ..., \omega^{n-1}\}$ are called the **n-th roots of unity** because they are the $n$ complex solutions to the equation $z^n = 1$.

They are placed **equally spaced on the unit circle**, representing the vertices of a regular $n$-gon.

<div align="center">
  <img src="path/to/your/image.png" alt="Roots of Unity diagram" width="600"/>
</div>

The figure above shows:
- Left: Roots of unity for $n = 3$
- Right: Roots of unity for $n = 6$
- Top half: counterclockwise ordering using $\omega = e^{2\pi i/n}$
- Bottom half: clockwise ordering using $\xi = e^{-2\pi i/n}$

We also have:

$$
\xi^{-k} = \overline{\xi^k} = \omega^k
$$

which is useful in DFT theory, especially when proving symmetry and inverse properties.


## 📂 Folder Structure

```bash
.
├── audio/
│   ├── noisy_sample.wav
│   └── clean_output.wav
├── notebooks/
│   └── denoise_dft_demo.ipynb
├── README.md
└── requirements.txt

