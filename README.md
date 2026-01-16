# GeneDIY-C: Site-Directed Mutagenesis & Seamless Cloning Primer Designer

![Version](https://img.shields.io/badge/Version-1.7-blue?style=flat-square)
![Author](https://img.shields.io/badge/Author-Jack%20Chang-green?style=flat-square)
![Platform](https://img.shields.io/badge/Platform-Web%20(Offline)-orange?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-purple?style=flat-square)

**GeneDIY-C** is a lightweight, single-file, offline web tool designed for molecular biology researchers. It integrates intelligent primer design for **Site-Directed Mutagenesis (SDM)**, **Multi-Site Mutagenesis** (via fragment assembly), and a built-in **Seamless Cloning Calculator**.

No installation, no server dependencies—just download and run in your browser.

---

## 🚀 Key Features

### 1. Flexible Mutation Modes
- **Single-Site Mutagenesis:** Supports single base substitution, multi-base substitution (up to 6bp), amino acid changes (with codon optimization), insertions (up to 10bp), and deletions.
- **Multi-Site Mutagenesis:** Automatically splits the plasmid into multiple PCR amplicons based on mutation sites, allowing for one-step assembly of multiple mutations using seamless cloning principles.

### 2. Smart Algorithms
- **Partial Overlap Strategy:** Utilizes a robust design strategy where primers have a 5' overlapping region (containing the mutation) and a 3' binding extension. [cite_start]This ensures high PCR efficiency and successful circularization[cite: 8, 19].
- **Automated Tm Optimization:** Uses the **Nearest Neighbor (NN)** thermodynamic model (SantaLucia 1998) with salt corrections ($Na^+$, $Mg^{2+}$). The tool automatically adjusts the primer extension length to match a target Tm (default ~35°C for the binding region).

### 3. Lab Utilities
- **Seamless Cloning Calculator:** Integrated into the Multi-Site mode. [cite_start]It automatically populates fragment lengths and calculates the required volumes for vector and inserts based on your desired molar ratio (e.g., 1:2)[cite: 137, 138].
- **Dynamic Visualization:** Real-time rendering of the plasmid map using HTML5 Canvas, showing mutation sites, primer binding positions, and PCR amplicon coverage.
- **Data Export:** One-click export to `.csv` (Excel compatible) containing primer sequences, Tm values, lengths, and fragment details.

---

## 🔬 Scientific Principles

### 1. Primer Design Strategy (Partial Overlap)
[cite_start]Unlike traditional full-overlap (QuikChange) or back-to-back strategies, GeneDIY-C uses a **Partial Overlap** approach[cite: 74]:
- **Forward Primer:** `5' [Overlap Region] - [Mutation] - [Extension Region] 3'`
- **Reverse Primer:** `5' [Overlap RC] - [Mutation RC] - [Extension RC] 3'`

**Mechanism:** The 5' ends of the primers contain the mutation and overlap with each other, while the 3' ends bind specifically to the template. The resulting PCR products have homologous ends that can be assembled via seamless cloning (Gibson Assembly, NEBuilder, etc.) or recircularized via KLD reaction.

### 2. Multi-Site Assembly Logic
For $N$ mutation sites, the tool divides the vector into $N$ PCR amplicons:
- **Fragment 1:** Amplifies from Mutation A (Fwd) to Mutation B (Rev).
- **Fragment 2:** Amplifies from Mutation B (Fwd) to Mutation C (Rev).
- ...and so on. The final fragments are assembled *in vitro*.

### 3. Reaction Calculator Formula
[cite_start]Based on the law of conservation of moles[cite: 144]:
$$\text{Mass}_{\text{insert}} = \text{Mass}_{\text{vector}} \times \frac{\text{Length}_{\text{insert}}}{\text{Length}_{\text{vector}}} \times \text{Molar Ratio}$$

---

## 🛠️ Quick Start

### Installation
This is a pure static HTML application.
1.  Download the `index.html` file from the [Releases](#) or source code.
2.  Double-click to open it with any modern web browser (Chrome, Edge, Firefox, Safari).
3.  **No internet connection required.** All logic runs locally.

### Workflow

#### A. Single-Site Mutagenesis
1.  Paste your plasmid sequence (5'->3').
2.  Select **"Single Site"** mode.
3.  Use the slider to locate the mutation site and select the mutation type (e.g., Amino Acid Change).
4.  Click **"Generate Primers & Map"**.
5.  View results and export to CSV.

#### B. Multi-Site Mutagenesis & Calculation
1.  Select **"Multi-Site"** mode.
2.  Configure your first mutation parameters and click **"+ Add Current Mutation"**.
3.  Repeat to add all desired mutation sites (at least 2).
4.  Click **"Generate Primers & Map"**. The tool will generate primer pairs for each amplicon.
5.  Scroll down to the **"Seamless Cloning Calculator"**, enter your vector mass and desired molar ratio, and click **"Calculate"** to get your pipetting volumes.

---

## 📦 Changelog

### V1.7 (Latest)
- **New:** Integrated **Seamless Cloning Calculator** for multi-site workflows.
- **New:** Auto-population of amplicon lengths into the calculator.
- **UI:** Refined interface; calculator appears dynamically after generation.

### V1.6
- **New:** Introduced **Multi-Site Mutagenesis** logic (Fragment Assembly).
- **Update:** Enhanced Canvas visualization to show multiple PCR fragments.

### V1.5
- **Update:** Rebranded to **GeneDIY-C**.
- **Meta:** Added author information.

### V1.0 - V1.4
- Core SDM functionality implementation.
- Tm optimization algorithm.
- Strict input validation and CSV export fixes.

---

## 📜 License & Author

- **Author:** Jack Chang
- **License:** MIT License
- **Copyright:** © 2026 GeneDIY-C

---

*If you find any bugs or have feature requests, please feel free to open an issue.*
