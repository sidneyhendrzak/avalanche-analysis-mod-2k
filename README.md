# Avalanche Analysis of y = (a * x + b) mod 2^k

This project studies the avalanche effect and Strict Avalanche Criterion (SAC) for linear congruential-style functions of the form

y = (a * x + b) mod 2^k

where x, a, b are integers and all arithmetic is done modulo 2^k. 

## Goal

Evaluate how sensitively the output bits of y respond to single-bit flips in the input x, for different choices of a and b and different bit-lengths k. This is a standard property studied in coding theory and cryptography. 

## Method

- For each bit-length k, set N = 2^k and iterate over all x in {0, …, N - 1}. 
- For each input bit i:
  - Flip bit i of x to get x_flipped.
  - Compute y = (a * x + b) mod N and y_flipped = (a * x_flipped + b) mod N.
  - Convert both outputs to k-bit vectors and record which output bits changed. 
- Accumulate counts in a SAC matrix of shape (k, k), where rows are output bits and columns are input bits. 
- Compute:
  - Average number of output bits that change per single input-bit flip.
  - SAC matrices as proportions (how often each output bit flips when each input bit is toggled). 

## What the Code Does

- Implements helper functions:
  - `int_to_bits(x, k)`: converts an integer to a length-k bit vector. 
  - `avalanche_analysis(k)`: runs the full experiment for a given k. 
- Loops over multiple odd multipliers a and all possible offsets b to explore parameter choices.
- Prints, for each (a, b) pair:
  - `avg_bits_changed`
  - The SAC matrix (rows = output bits, cols = input bits) rounded to 3 decimals. 

## Example Output

For k = 3 and selected (a, b) pairs, we print lines like: 

- `a=3, b=0, avg_bits_changed=1.667`
- Corresponding 3x3 SAC matrix of flip probabilities for each output bit vs. each input bit. 

For k = 4, we obtain 4x4 SAC matrices and average bit changes around 1.7–2.1, depending on the parameters, and can visually see which parameter sets spread changes more uniformly across output bits. 

## How to Run

1. Clone or download this repository.
2. Open `549_Final.ipynb` (or `AvalancheAnalysis.ipynb`) in Jupyter or Google Colab.
3. Run all cells.
4. Inspect the printed `avg_bits_changed` values and SAC matrices for different (a, b) and k. 

## Skills Demonstrated

- Bitwise operations and binary representations in Python.
- Exhaustive enumeration and algorithmic analysis over all inputs x in a finite space. 
- Measuring and interpreting avalanche behavior and SAC, concepts relevant to coding theory and cryptography. 
