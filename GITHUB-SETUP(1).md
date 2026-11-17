# GitHub Repository Publishing Guide

**Suggested GitHub repository name**: `quantum-circuit-fundamentals-qiskit`

**Suggested description**: Reproducible Qiskit circuits (1–8 qubits): superposition, Bell/GHZ states, seeded random circuits, and ideal simulation.

**Suggested topics**: `qiskit`, `quantum-computing`, `quantum-circuits`, `quantum-simulation`, `ghz-state`, `bell-state`, `jupyter-notebook`, `python`

## Publish to GitHub

1. Sign in to the GitHub account `70182617-ai`.
2. Open [Create a new repository](https://github.com/new).
3. Enter `quantum-circuit-fundamentals-qiskit` as the name, add the description above, and choose whether the repository will be **Public** or **Private**.
4. **Do not** add a second README, `.gitignore`, or license from the GitHub setup screen: these files are already in the downloaded folder.
5. From a terminal inside the extracted project folder, run:

```bash
git init
git add .
git commit -m "Initial commit: reproducible Qiskit 1–8 qubit circuits"
git branch -M main
git remote add origin https://github.com/70182617-ai/quantum-circuit-fundamentals-qiskit.git
git push -u origin main
```

6. On GitHub, select **About > Settings** to add the suggested topics, and consider enabling GitHub Actions. The included workflow checks notebooks and unit tests on each push/PR.

## Before publishing

- Confirm that **Muhammad Yasin** is the correct author credit in `README.md`, `CITATION.cff` and `LICENSE`.
- Confirm that the **MIT License** is the reuse permission you want to grant. It permits reuse and modification (including commercially), subject to attribution and license terms. If you prefer a different license, change it before making the repository public.
- The notebooks contain ideal simulation examples. Do not describe them as runs on IBM or IQM hardware.
- The repository code path in `CITATION.cff` assumes the name and account listed above. Update it if you choose another name.
