# Quantum Circuit Fundamentals with Qiskit: 1-8 Qubits

Reproducible quantum circuit demonstrations: superposition, Bell and GHZ states, and seeded random circuits.

A compact Qiskit project exploring 1-8 qubit circuits with ideal, shot-based simulation. The two notebooks move from deliberately prepared quantum states to configurable pseudo-random gate sequences, and include circuit diagrams, measured bitstring counts and histograms.

Scope: These are ideal simulations using StatevectorSampler. They are not runs on IBM Quantum or IQM hardware, not quantum error-correction experiments, and not device-calibrated noise models.

## Notebooks

| Notebook | Coverage | Core idea | Shots per circuit |
|---|---|---|---:|
| 01 State preparation and GHZ | 1-8 qubits | Hadamard superposition, Bell state, GHZ states | 1,024 |
| 02 Seeded random circuits | 1-8 qubits | Seeded Qiskit random circuits with varying depth and gate arity | 4,096 |

## Quick start

Requirements: Python 3.10 or newer (3.11 recommended), pip, and Jupyter or Google Colab.

Clone the repository and install the pinned dependencies:

```
git clone https://github.com/70182617-ai/quantum-circuit-fundamentals-qiskit.git
cd quantum-circuit-fundamentals-qiskit
python -m pip install "qiskit[visualization]==2.5.2" matplotlib
jupyter lab
```

Open a notebook from the notebooks folder and select Run All.

Google Colab: upload either notebook, install qiskit[visualization]==2.5.2 and matplotlib in the session, and run all cells.

## Methodology

A single-qubit Hadamard gate prepares the equal superposition of |0> and |1>. For n of at least 2, a Hadamard gate on qubit 0 followed by a chain of CNOT gates prepares the GHZ state (|0...0> + |1...1>) divided by the square root of 2. For n = 2 this is the Bell state. Ideal measurement should return 00...0 and 11...1 with probability 1/2 each. The notebooks check the ideal simulated statevector before measurement. Measurement counts alone do not certify entanglement, because a classical mixture can produce the same histogram.

The second notebook uses qiskit.circuit.random.random_circuit with deterministic seeds (101 through 808 in steps of 101), generation depths of 10, 12 or 14, up to four gate operands, and terminal computational-basis measurements. It reports the actual circuit depth, operation counts and sampled bitstring frequencies. The requested generation depth is not necessarily the final depth after measurement. A random circuit does not imply uniform outcomes or hardware-native executability.

## Reproducibility

Qiskit StatevectorSampler performs ideal statevector-based sampling, not device-noise simulation. The random generator and the sampler are seeded, so runs are repeatable on the same package version. Counts are finite-shot samples, not exact probabilities. The notebooks use Qiskit 2.5.2.

## Limitations and future directions

These demonstrations are an educational and reproducibility-oriented foundation. They are not a quantum error-correction result or a peer-reviewed study. Natural extensions include hardware-native transpilation, a calibrated noise model, entanglement verification and comparison with real-device results. Each of these must be evaluated separately.

## Author

Muhammad Yasin, Physics and Quantum Computing.
