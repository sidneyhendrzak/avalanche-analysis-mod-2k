## Notebooks in This Repository

### 1. Avalanche_Final.ipynb (Recommended Entry Point)

A concise, self-contained implementation of avalanche analysis for linear congruential-style functions

y = (a * x + b) mod 2^k

- Converts integers to k-bit vectors (`int_to_bits`, `bits_to_int`). 
- Defines `linear_sub_cipher(x, a, b, N)` for N = 2^k. 
- For each odd a (3 ≤ a ≤ N-1) and all b:
  - Flips each input bit of x.
  - Recomputes the output and counts how many output bits change.
  - Computes the **average number of output bits flipped** (avalanche measure) for each (a, b) pair. 
- Runs:
  - Full analysis for k = 3 (all keys).
  - Sampled-key analysis for k = 4 to keep computation reasonable. 

This notebook is the best place for employers to quickly understand the experiment and see clear numerical results.

### 2. 549_Final.ipynb (Extended SAC Analysis)

A more detailed version that, in addition to average bit flips, computes **Strict Avalanche Criterion (SAC) matrices**:

- Exhaustively flips each input bit for all x in {0, …, 2^k - 1}. 
- Builds SAC matrices (rows = output bits, cols = input bits), showing the proportion of times each output bit flips when each input bit is toggled. 
- Runs experiments for multiple k and across different (a, b) values, printing average MAE-style metrics and SAC matrices.

## How to Run

1. Clone or download this repository.
2. Open either:
   - `Avalanche_Final.ipynb` for a quick, readable avalanche analysis, or 
   - `549_Final.ipynb` for the extended SAC matrix experiments. 
3. Run all cells in your Python environment (Jupyter or Google Colab).
4. Inspect:
   - For `Avalanche_Final.ipynb`: printed lines like `a=3, b=0, Average Output Bits Flipped: 1.667`.
   - For `549_Final.ipynb`: average bits changed and full SAC matrices per (a, b) and k. 

