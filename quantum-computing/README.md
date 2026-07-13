# Quantum Computing Resources

This folder contains the quantum computing learning track and its core books.

## Folder Layout

- [books/](books/README.md): Core quantum books in recommended reading order.

## Objective

Develop competency in quantum foundations, circuit design, and introductory algorithms through coordinated reading, lectures, and implementation.

## Required Setup

- Python 3.10+
- Qiskit
- Jupyter Notebook
- IBM Quantum account: https://quantum.ibm.com/

```bash
pip install qiskit jupyter
jupyter notebook
```

## Study Plan

### 1. Foundations

Focus:

- Qubits
- Superposition
- Entanglement
- Basic gates (H, X, CNOT)

Reading:

- [Quantum Computing for Everyone](books/quantum-computing-for-everyone.pdf)

Practice:

- Single-qubit Hadamard experiment
- Bell state preparation and measurement

### 2. Circuit Programming

Focus:

- Circuit construction in Qiskit
- Measurement and interpretation
- Multi-qubit systems

Reading:

- [Programming Quantum Computers: Essential Algorithms and Code Samples](books/programming-quantum-computers-essential-algorithms-and-code-samples.pdf)

Practice:

- Quantum coin toss
- Bell state generator
- Quantum teleportation (simulation)

### 3. Introductory Algorithms

Focus:

- Grover's algorithm
- Shor's algorithm (conceptual and small-scale simulation)
- Quantum Fourier Transform (QFT)

Reading:

- [Quantum Computing: A Gentle Introduction](books/Quantum%20Computing%20A%20Gentle%20Introduction%20%E2%80%94%20Eleanor%20Rieffel.pdf)

Practice:

- Grover search implementation
- Small-number Shor simulation

### 4. Applied Topics

Focus:

- Optimization use cases
- Introductory quantum machine learning
- Industry-oriented demonstrations

Reading:

- [Quantum Computing: An Applied Approach](books/Quantum%20Computing%20An%20Applied%20Approach%20by%20Jack%20D.%20Hidary.pdf)

Practice:

- Portfolio optimization toy model
- Quantum random number generator
- Hybrid classical ML + quantum demo

### 5. Advanced Reference (Optional)

- [Quantum Computation and Quantum Information](books/quantum-computation-and-quantum-information-nielsen-chuang.pdf)

Use this text as a long-term reference rather than an introductory first pass.

## Recommended Work Pattern

- 1-2 hours per day, 5-6 days per week
- Suggested distribution: 40% coding, 30% video lectures, 30% reading

## Deliverables

By completion, prepare the following portfolio artifacts:

1. Hadamard and measurement notebook
2. Bell state and entanglement notebook
3. Quantum teleportation notebook
4. Grover implementation notebook
5. Small-number Shor notebook
6. One applied project notebook

## Resources

Primary resources are listed in [books/README.md](books/README.md), including short summaries of what each book covers.
