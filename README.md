# 🧬 Automated GROMACS 10 ns Molecular Dynamics Simulation Pipelin

[![Kaggle](https://img.shields.shields.io/badge/Kaggle-Notebook-blue?style=for-the-badge&logo=kaggle)](https://www.kaggle.com/code/mdhasibulhossain434/before-the-storm?scriptVersionId=325403814)
[![License: MIT](https://img.shields.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

An end-to-end structural bioinformatics workflow implemented in Python and Bash for automating **10 ns production Molecular Dynamics (MD) simulations** of peptide-protein complexes using **GROMACS**. 

---

### 📊 Structural Stability Analysis Summary
The pipeline automatically extracts simulation matrices and generates high-resolution analytical dashboards to evaluate trajectory physics:

* **Root Mean Square Deviation (RMSD):** Evaluates the structural equilibration and stability of the protein backbone over the 10 ns timeline compared to both the initial crystal structure and the equilibrated state.
* **Radius of Gyration (Rg):** Tracks the structural compactness and folding integrity of the macromolecular architecture throughout the high-temperature dynamic runs.
* **Hydrogen Bonding Profiler:** Quantifies real-time mainchain, sidechain, and solvent interaction counts.
* **DSSP Mapping:** Automates secondary structure transition profiles over time.

---

## 🛠️ Infrastructure & Environment Setup
The pipeline is natively configured to harness cloud-based GPU infrastructure (such as Kaggle or Google Colab Kernels), eliminating local dependency constraints.

* **Force Field:** AMBER99SB-ILDN
* **Water Model:** Explicit TIP3P Solvation
* **Hardware Integration:** GPU Accelerated (NVIDIA T4 / P100) with LinCS constraint optimizations
* **Environment Manager:** Micromamba / Conda Virtual Environments

---

## 📁 Repository Blueprint
```text
├── .gitignore               # Prevents multi-gigabyte binary trajectories from bloating Git
├── LICENSE                  # MIT Permissive License
├── README.md                # Comprehensive documentation frontpage
└── before-the-storm.ipynb   # Master executed notebook with source code, logs, and plots
```
💻 How to Run This Pipeline on Kaggle (With Your Own Data)

If you wish to replicate this simulation workflow or adapt it for a different protein-ligand complex, use the following guide:
Step 1: Import the Workspace

    Download the before-the-storm.ipynb file from this repository.

    Log into your account at Kaggle.com.

    Navigate to Code ➡️ New Notebook.

    In the editor menu, go to File ➡️ Import Notebook and upload your downloaded .ipynb file.

Step 2: Configure Compute Settings

GROMACS workloads demand specialized hardware. In the Kaggle settings panel (right sidebar):

    Toggle Accelerator and select GPU T4 x2 or GPU P100.

    Toggle the Internet switch to On (Mandatory for compiling GROMACS dependencies and Micromamba installations).

Step 3: Populate Input Dataset

    Click Add Input in the top-right data panel.

    Select Upload a Dataset, drop your structural complex file (e.g., dla_complex.pdb), and initialize it.

    Once compiled, copy the exact input directory path from the file viewer panel.

Step 4: Map the Configuration Variables

Open the notebook, locate the primary Bash Configuration Cell (Cell 4/5), and update the INPUT_PDB placeholder variable with your copied path:
```
# =====================================================================
# 📁 CONFIGURATION: Set your unique Kaggle input path here
# =====================================================================
INPUT_PDB="/kaggle/input/YOUR_KAGGLE_USERNAME/YOUR_DATASET_NAME/your_file.pdb"
CLEAN_PDB="/kaggle/working/dla_clean.pdb"
```
The workflow will automatically abstract this entry, strip crystallographic water molecules (HOH), dynamically calculate box constraints (1.2 nm cubic space), auto-neutralize system net charges via ion substitution, and process the 10 ns trajectory.
Step 5: Execute & Fetch Analytics

    Click Save & Run All to run the pipeline sequentially in the cloud background.

    Upon termination, the script automatically packs all checkpoint configurations, logs, and structural figures into a clean simulation_output.zip archive available in your workspace output panel.

⚖️ License

Distributed under the MIT License. See LICENSE for more information. Any academic or computational use of this automated blueprint is highly welcome.
