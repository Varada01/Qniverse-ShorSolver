# Qniverse-ShorSolver
# 🔓 Qniverse ShorSolver

A universal, scalable implementation of **Shor’s Quantum Factoring Algorithm** built by Team **Qniverse** for the **Quantum Factorization Challenge @ YQuantum 2025**.

This project demonstrates how quantum computing can efficiently factor large semiprime numbers using **200-qubit support on Quantum Rings**, showcasing a practical advantage over classical algorithms.

---

## Project Highlights

- **Universal Shor's Algorithm**: Supports factoring arbitrary semiprimes (not hardcoded).
- **Modular Exponentiation**: Built using repeated squaring, with efficient quantum arithmetic.
- **Phase Estimation & QFT**: Dynamically scales the counting register for precise period finding.
- **Classical Post-Processing**: Extracts period `r` and computes GCDs to find the semiprime factors.
- **Smart 'a' Selector**: Strategically picks values of `a` for better success probability.
- **Quantum Rings SDK Optimized**: Uses native gates, mid-circuit measurement, and qubit reuse for scalability up to **200 qubits**.

---

##  How It Works

1. **Pick a value `a`** randomly such that `1 < a < N`
2. **Build quantum circuit**:
   - Apply Hadamards to counting register
   - Perform **controlled modular exponentiation**: `a^x mod N`
   - Apply **inverse Quantum Fourier Transform**
   - Measure and extract period `r`
3. **Classical check**:
   - Compute `gcd(a^(r/2) ± 1, N)`
   - If `0 < factor < N` → success!
4. **Repeat if needed** with new `a` values

---

##  Results

| Semiprime | Qubits Used | Factors Found | Runtime |
|-----------|-------------|----------------|---------|
| 15        | 6           | 3, 5           | ✅       |
| 21        | 8           | 3, 7           | ✅       |
| 91        | 16+         | 7, 13          | ✅       |
| 🔒 ???    | 🚀 ~200      | TBD (target)   | 🧪 In Progress |

---

## 🛠 Setup & Usage

> **Note:** Requires access to Quantum Rings platform. Supports QASM import if using Qiskit or Cirq.

```bash
git clone https://github.com/QniverseTeam/Qniverse-ShorSolver.git
cd Qniverse-ShorSolver

# Install dependencies
pip install -r requirements.txt

# Run the factoring algorithm
python shor_solver.py --n 91
