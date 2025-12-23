# Quantum-Error-Correction-Codes
![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Cirq](https://img.shields.io/badge/Framework-Cirq%20Google-green)
![Cirq](https://img.shields.io/badge/Framework-Qiskit%20IBM-purple)
![Status](https://img.shields.io/badge/Status-Educational%20%2F%20Research-orange)

## 📖 Project Overview

This repository documents a practical study of **Quantum Error Correction (QEC)** protocols, culminating in the implementation of the **Surface Code** on a simulation of Google's **Willow** quantum processor.

The project simulates the `willow_pink` device architecture, utilizing realistic noise models, connectivity topologies, and calibration data provided by the `cirq-google` framework. The goal was to understand how theoretical error correction codes (like Shor's Code and Surface Codes) translate to physical hardware with specific constraints and native gate sets.

## 🚀 Key Features

* **Hardware Analysis:** Inspection of the Willow processor's T1 times, gate fidelity, and qubit connectivity graph.
* **Native Compilation:** All circuits are transpiled to the device's native gateset (e.g., `PhasedXZ`, `CouplerPulse`) to ensure realistic execution metrics.
* **Incremental Complexity:** The repository follows a learning path from simple error detection to topological error correction.
* **Visualization:** extensive use of `networkx` for topology mapping and `SVGCircuit` for circuit inspection.

## 📂 Repository Structure

The notebooks are organized by complexity, guiding the reader through the fundamentals of QEC up to topological codes.

| File | Description |
| :--- | :--- |
| **`Willow_Processors_Specifications.ipynb`** | **Hardware Baseline.** Connects to the `willow_pink` engine, analyzes $T_1$ coherence times, visualizes the chip topology, and runs a Bell State experiment to test entanglement fidelity. |
| **`Two Qubits Error Detection Code [[2, 1 ,2]].ipynb`** | **Basic Detection.** Implementation of a simple code capable of detecting single errors using parity checks. |
| **`Three Qubits Error Correction Code [[3, 1, 3]].ipynb`** | **Bit-Flip Correction.** A classic repetition code that encodes 1 logical qubit into 3 physical qubits to correct bit-flip errors via majority voting. |
| **`The [[4, 2, 2]] Error Detection Code.ipynb`** | **Error Detection.** Implementation of a code that encodes 2 logical qubits into 4 physical ones, capable of detecting any single-qubit error. |
| **`The Shor [[9, 1, 3]] Code.ipynb`** | **Full Correction.** The famous Shor Code implementation. It concatenates bit-flip and phase-flip codes to protect against arbitrary single-qubit errors ($X$ and $Z$). |
| **`The_Surface_Code.ipynb`** | **Topological QEC (Advanced).** The core of this project. Defines a logical patch on the Willow grid, assigns Data/Ancilla roles (Checkerboard pattern), builds the stabilizer cycle, and extracts syndrome vectors for decoding. |

## 🧠 Theoretical Background

The implementation of the Surface Code in this repository relies on the concept of **Stabilizer Formalism** and **Toric/Planar Codes**. Specifically, the simulation constructs a logical qubit by defining:
* **Data Qubits:** Vertices of the lattice.
* **X-Stabilizers (Ancilla):** Measure phase parity (vertex operators).
* **Z-Stabilizers (Ancilla):** Measure bit-flip parity (plaquette operators).

### References
This project was designed and implemented based on the study of the following papers/articles:
1.  *[Quantum Error Correction: An Introductory Guide] - [arXiv:1907.11157]*
2.  *[Surface codes: Towards practical large-scale quantum computation] - [arXiv:1208.0928]*
