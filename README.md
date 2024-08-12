**Quantum Harmonic Oscillator Simulation using Qiskit**


This project demonstrates the simulation of a Quantum Harmonic Oscillator using the Qiskit framework. The code uses Qiskit to build a quantum circuit that approximates the ground state energy of a simple quantum harmonic oscillator through variational quantum eigensolver (VQE) techniques.

Introduction
The quantum harmonic oscillator is a fundamental model in quantum mechanics, representing systems such as vibrational modes in molecules and phonons in solids. The Hamiltonian for a quantum harmonic oscillator is typically expressed as:


where:

𝑝
^
p
^
​
  is the momentum operator,
𝑚
m is the mass of the particle,
𝜔
ω is the angular frequency,
𝑥
^
x
^
  is the position operator.

In this code, we approximate the Hamiltonian using quantum circuits and solve for the ground state energy using a variational approach.

Mathematical Formulation
The code maps the fermionic operators to qubit operators using the Jordan-Wigner transformation. The Hamiltonian is then expressed in terms of Pauli matrices, which are used to construct the quantum circuit. The variational quantum eigensolver (VQE) method is used to minimize the expectation value of the Hamiltonian:

⟨
𝜓
(
𝜃
)
∣
𝐻
^
∣
𝜓
(
𝜃
)
⟩
⟨ψ(θ)∣ 
H
^
 ∣ψ(θ)⟩

where 
∣
𝜓
(
𝜃
)
⟩
∣ψ(θ)⟩ is the trial wavefunction parameterized by the angles 
𝜃
θ. The minimization is carried out using the COBYLA optimization method.

Code Overview
Quantum Circuit Construction
Initialization:

A quantum circuit is created with one qubit, initialized with a Hadamard gate followed by an RX rotation gate. This circuit serves as the initial state for the simulation.
Hamiltonian:

The fermionic Hamiltonian is mapped to a qubit operator using the Jordan-Wigner Mapper. This operator is then used as the observable in the VQE calculation.
Ansatz:

The ansatz is created using the RealAmplitudes class, which generates a parameterized quantum circuit.
Transpilation
The circuit is transpiled using a preset pass manager to optimize the circuit for a specific backend (in this case, the AerSimulator).
Estimator and Optimization
The Estimator primitive is used to evaluate the expectation value of the Hamiltonian.
A custom cost_func is defined to compute the energy, which is minimized using the COBYLA optimizer.
Cost Function
The cost_func evaluates the energy of the system using the provided parameters. It also tracks the optimization history, including the number of iterations and the cost at each step.

Output
The result of the minimization is printed, showing the optimized parameters and the corresponding ground state energy.
A plot of the cost function over iterations is generated to visualize the convergence of the optimization process.
Running the Code
To run this simulation:

Install the required dependencies, including Qiskit and a compatible Python environment.
Run the provided Python script. The script uses Qiskit's AerSimulator for simulation, but can be configured to run on actual quantum hardware by changing the backend.
Conclusion
This code provides a basic implementation of simulating a quantum harmonic oscillator using Qiskit's VQE framework. The results approximate the ground state energy of the oscillator, demonstrating the potential of quantum computing for solving quantum mechanical problems.
