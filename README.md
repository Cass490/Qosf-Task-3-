# Quantum Computing Solutions for Bin Packing Problem

## Introduction

### Problem Statement
The Bin Packing Problem (BPP) is a classic optimization challenge where items of different weights must be packed into a minimum number of fixed-capacity bins. This implementation explores various quantum computing approaches to solve BPP.

## Implementation Overview

### 1. Problem Formulation
- Started with Integer Linear Programming (ILP) formulation
- Transformed ILP to Quadratic Unconstrained Binary Optimization (QUBO)
- Created test instances of varying sizes: small, medium and large

### 2. Solution Approaches Implemented

#### Classical Approach
- Brute Force solver
  - Guaranteed optimal solution for small instances
  - Execution time: 0.02s (small) → 6,628s (medium)
  - Becomes infeasible for large instances

#### Quantum Approaches

1. **Quantum Annealing**
   - Results:
     - Small Instance: -75,000 (4.2s)
     - Medium Instance: -196,000 (4.3s)
     - Successfully handled large instances
   - Consistent execution times across problem sizes

2. **Variational Quantum Eigensolver (VQE)**
   - Results:
     - Small Instance: -7,000 (0.48s)
     - Medium Instance: -60,000 (244s)
     - Unable to process large instances
   - Showed significant scaling issues

3. **Quantum Approximate Optimization Algorithm (QAOA)**
   - Results:
     - Small Instance: -2,823 (1.72s)
     - Medium Instance: -29,047 (511s)
     - Unable to process large instances
   - Poorest solution quality among quantum approaches

## Performance Analysis
 
1.  ### The Brute Force Classical Solver
- Small Instance: Its nearly instantaneous execution duration of 0.02 seconds shows how effective it is with little computational burden.
- Medium Instance: As the execution time sharply increases to 6,628 seconds, the complexity shows exponential growth.
- Large Instances: The exponential growth of the solution space (O(2^n)), where n is the number of elements, renders brute force computationally impractical. This outcome demonstrates the serious drawbacks of the classical method in more complex BPP scenarios.
  
The brute force method systematically explores the entire solution space to guarantee the global optimum which is why it yields the best result for small instance due to its simplicity and lack of setup overhead. However,it becomes infeasible as the problem scales due to exponential growth (O(2^n)).

2. ### Quantum Annealing 
- Small, Medium, and Large Instances: Across a range of problem sizes, the execution time stays very consistent at about 4 seconds.
- The D-Wave system's architecture, which is ideal for QUBO formulations, allows quantum annealing to maintain steady performance. Because of its consistency, it is the most scalable approach, handling larger instances that are difficult for variational and brute force methods to manage.
  
Quantum annealing stands out as a powerful approach for solving BPP across a wide range of sizes as leverages D-Wave's adiabatic computation model, which efficiently handles larger BPP instances due to its resilience against combinatorial explosion achieving efficient and high-quality solutions while exhibiting a constant time complexity.

3. ### Quantum Variational Eigensolver (VQE)
- Small Instance: This approach takes reasonable execution time (at 0.48 seconds) with competitive solution quality, showing VQE's potential for small problem sizes.
- Medium Instance: The execution time increased significantly (to 244 seconds), indicating the method's sensitivity to circuit depth and the necessity for more qubits as the problem size increases.
- Large Instances: The inability to optimize parameters and the difficulty of preserving fidelity over deeper circuits make VQE impractical for large instances.
  
It can be seen that VQE can only be used in smaller BPP instances due to its scaling problems. Effective scaling is hindered by the need for circuit depth and parameter optimization, even though it offers a respectably good solution quality for small cases.

4. ### Quantum Approximate Optimization Algorithm (QAOA)
- Small Instance: The solution is achieved in 1.72 seconds, although the quality of the solution (-2,823) is not as good as other quantum methods.
- Medium Instance: As more qubits are needed, the execution time increases to 511 seconds, indicating scalability problems.
- Large Instances: Because controlling the parameterized layers gets more difficult and the quality decreases as a result, QAOA is not feasible for large instances.
  
Compared to Quantum Annealing, QAOA exhibits potential for small to medium instances but suffers in terms of solution quality and scalability. Its practical applicability to bigger instances is further limited by difficulties with parameter adjustment and fidelity concerns.

## Technical Implementation Details

### QUBO Formulation
- Successfully transformed BPP from ILP to QUBO
- Tested across multiple instance sizes
- Verified formulation correctness with brute force results

### Quantum Circuit Implementation
- Multiple ansatz designs tested for VQE
- Custom QAOA implementation
- Hybrid quantum-classical optimization approach

## Conclusions

1. **Best Approach**: Quantum Annealing emerged as the most practical solution
   - Consistent performance
   - Scalable to larger problems
   - Best solution quality

2. **Algorithmic Insights**:
   - VQE and QAOA show potential but need improvements
   - Parameter optimization remains a challenge
   - Circuit depth limitations affect performance

3. **Scaling Behavior**:
   - Clear advantage of quantum annealing in scaling
   - Traditional approaches hit exponential wall
   - VQE/QAOA face significant scaling challenges



## Requirements
- Python 3.x
- D-Wave Ocean SDK
- Qiskit
- Pennylane
- NumPy
- Docplex (for ILP formulation)
