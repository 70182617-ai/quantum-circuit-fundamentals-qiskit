# Quantum Circuit Fundamentals with Qiskit: 1–8 Qubits

**Reproducible quantum circuit demonstrations: superposition, Bell/GHZ states, and seeded random circuits.**

A compact, research-minded Qiskit portfolio project exploring **1–8 qubit circuits** with ideal shot-based simulation. The two notebooks move from deliberately prepared quantum states to configurable pseudo-random gate sequences, and include circuit visualizations, measured bitstring counts and histograms.

> **Scope:** These are ideal *simulations* using `StatevectorSampler`; they are **not** real IBM Quantum or IQM hardware runs, quantum error-correction experiments, device-calibrated noise models, or demonstrations of quantum advantage.

## Overview

| Notebook | Coverage | Core idea | Shots per circuit |
| --- | --- | --- | ---: |
| [01 · State preparation and GHZ](notebooks/01-state-preparation-and-ghz-1-to-8-qubits.ipynb) | 1–8 qubits | Hadamard superposition; Bell state; GHZ states | 1,024 |
| [02 · Seeded random circuits](notebooks/02-seeded-random-circuits-1-to-8-qubits.ipynb) | 1–8 qubits | Seeded Qiskit random circuits, varying depths and gate arity | 4,096 |

### Circuit previews

| Bell-state circuit | Bell-state measurement counts |
| --- | --- |
| ![Two-qubit Bell state circuit](assets/bell-state-circuit.png) | ![Two-qubit Bell state sampled histogram](assets/bell-state-histogram.png) |

![Eight-qubit GHZ circuit](assets/eight-qubit-ghz-circuit.png)

A four-qubit seeded random circuit from the second notebook:

![Four-qubit seeded random circuit](assets/seeded-random-four-qubit-circuit.png)

*Images are snapshots saved from the originally supplied notebook runs. Re-running the updated notebooks produces new plots; individual finite-shot counts may differ.*

## Quick start

Requirements: **Python 3.10+** (Python 3.11 recommended), pip, and Jupyter Notebook/Lab or Google Colab.

After creating and publishing the GitHub repository:

```bash
git clone https://github.com/70182617-ai/quantum-circuit-fundamentals-qiskit.git
cd quantum-circuit-fundamentals-qiskit
python -m venv .venv
```

Activate the virtual environment:

```bash
# macOS / Linux
source .venv/bin/activate
# Windows PowerShell: .venv\Scripts\Activate.ps1
```

Install and launch:

```bash
python -m pip install -r requirements.txt
jupyter lab
```

Open `notebooks/01-state-preparation-and-ghz-1-to-8-qubits.ipynb` or `notebooks/02-seeded-random-circuits-1-to-8-qubits.ipynb`, then select **Run All**.

**Colab:** Upload either notebook, install `qiskit[visualization]==2.5.2` and `matplotlib` in the session using `%pip`, and run all cells. A Colab runtime restart may be necessary after package installation.

## Methodology

### 1. Superposition, Bell states and GHZ states

For one qubit, a Hadamard gate prepares:

$$
|+\rangle = \frac{|0\rangle + |1\rangle}{\sqrt{2}}.
$$

For $n \ge 2$, a Hadamard on qubit 0 followed by a chain of CNOT gates generates:

$$
|\mathrm{GHZ}_n\rangle = \frac{|0\rangle^{\otimes n} + |1\rangle^{\otimes n}}{\sqrt{2}}.
$$

For $n=2$, this is the Bell state $|\Phi^+\rangle$. Measurement in the computational basis should ideally return `00...0` and `11...1`, each with probability 1/2. The notebook verifies the ideal simulated statevector before measurement. **Measurement counts alone do not certify entanglement**, because a classical mixture may yield the same histogram.

### 2. Seeded pseudo-random quantum circuits

The second notebook uses `qiskit.circuit.random.random_circuit` with deterministic seeds (`101` through `808` in steps of `101`), generation depths of 10, 12, or 14, up to four gate operands, and terminal computational-basis measurements. It reports actual circuit depth, operation counts, and sampled bitstring frequencies.

The requested generation depth is not necessarily the final depth after measurement operations. Also, "random circuit" refers to the gate-generation procedure; it does **not** imply uniform measurement outcomes or hardware-native executability.

### Simulator and reproducibility

- Qiskit `StatevectorSampler` performs ideal statevector-based sampling, not device-noise simulation.
- The random generator and the sampler are seeded. Counts are finite-shot samples, not exact probabilities.
- Notebooks use **Qiskit 2.5.2**, aligned with the supplied source notebooks.
- Simulation results can vary across package versions or RNG implementation changes; dependency pinning and seeds make reproduction more controlled.

## Project layout

```text
quantum-circuit-fundamentals-qiskit/
├── notebooks/
│   ├── 01-state-preparation-and-ghz-1-to-8-qubits.ipynb
│   └── 02-seeded-random-circuits-1-to-8-qubits.ipynb
├── assets/
│   ├── bell-state-circuit.png
│   ├── bell-state-histogram.png
│   ├── eight-qubit-ghz-circuit.png
│   └── seeded-random-four-qubit-circuit.png
├── tests/test_quantum_circuits.py
├── scripts/validate-notebooks.py
├── .github/workflows/validate.yml
├── requirements.txt
├── requirements-dev.txt
├── CITATION.cff
├── CONTRIBUTING.md
├── GITHUB-SETUP.md
├── LICENSE
└── README.md
```

## Validation

```bash
python -m pip install -r requirements-dev.txt
python scripts/validate-notebooks.py
pytest -q
```

The validator checks notebook formatting, Python syntax and cleared execution outputs. Unit tests cover mathematical GHZ state preparation, seeded random-circuit generation and ideal sampling invariants. GitHub Actions is configured to repeat these checks on push and pull requests.

## Limitations and future directions

These demonstrations form an **educational and reproducibility-oriented foundation**, not a novel QEC result or a peer-reviewed research study. Natural extensions include hardware-native transpilation, a calibrated noise model, entanglement verification, and comparison with real-device results; such extensions must be evaluated separately.

## Author and citation

**Muhammad Yasin** — Physics / Quantum Computing

If you use this repository in educational or research material, cite it as software using [`CITATION.cff`](CITATION.cff). This repository does not claim an associated journal publication or DOI.

## License

Distributed under the [MIT License](LICENSE). Qiskit is a separate project with its own license and attribution.

## References

- [IBM Quantum: Qiskit quickstart](https://quantum.cloud.ibm.com/docs/en/guides/quick-start)
- [IBM Quantum: StatevectorSampler API](https://quantum.cloud.ibm.com/docs/en/api/qiskit/qiskit.primitives.StatevectorSampler)
- [IBM Quantum: Sampler inputs and outputs](https://quantum.cloud.ibm.com/docs/en/guides/sampler-input-output)
- [Qiskit repository](https://github.com/Qiskit/qiskit)
