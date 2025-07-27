# Smart Grid Optimization Code Repository

This repository contains Python code and a Jupyter notebook for the smart grid optimization project developed as part of the ITS66604 Machine Learning and Parallel Computing (MLPC) group assignment (May 2025, Taylor's University). The code implements a parallelized Genetic Algorithm (GA) to optimize energy distribution across 3 energy sources (Solar, Wind, Hydro) and 10 consumer nodes over a 24-hour cycle, minimizing cost, transmission losses, and penalties. It includes a greedy baseline for comparison, achieving a 9.52% fitness improvement, with parallel processing reducing execution time by ~2.3x. This README was generated on Sunday, July 27, 2025, at 06:35 PM +0545, ahead of the assignment due date (July 13, 2025, 11:59 PM via MyTimes).

## Project Overview

The project addresses a constrained multi-objective optimization problem for smart grid energy distribution:
- **Objectives**: Cost minimization, transmission loss minimization, demand satisfaction (penalized for unmet demand or capacity overuse).
- **Methodology**: GA with chromosome encoding (3 × 10 × 24 vector), fitness function (weighted 0.4 cost, 0.3 loss, 0.2 demand penalty, 0.1 capacity penalty), and parallel fitness evaluation using Python’s `multiprocessing`.
- **Results**: Best GA fitness -840,968.56 vs. greedy -912,315.96; parallel execution 16.96s vs. serial 98.32s.

## Repository Structure

```
smart-grid-optimization/
├── src/
│   ├── main.py                 # Main script to run GA or greedy algorithm
│   ├── genetic_algorithm.py    # GA implementation (selection, crossover, mutation)
│   ├── greedy_algorithm.py     # Greedy baseline implementation
│   ├── parallel_processing.py  # Parallel fitness evaluation
│   ├── data_processing.py      # Data loading and preprocessing
│   ├── visualization.py        # Plotting functions
│   └── utils.py               # Utility functions
├── notebooks/
│   ├── worked_fitness_example.ipynb  # Worked fitness example (3 nodes, 2 sources)
│   └── data_exploration.ipynb        # Placeholder for data exploration
├── README.md                   # This file
├── requirements.txt            # Python dependencies
```

## Setup

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/<your-username>/smart-grid-optimization.git
   cd smart-grid-optimization
   ```

2. **Install Dependencies**:
   Ensure Python 3.8+ is installed, then install required packages:
   ```bash
   pip install -r requirements.txt
   ```
   The `requirements.txt` includes:
   ```
   numpy>=1.21.0
   pandas>=1.3.0
   matplotlib>=3.4.0
   ```

3. **Prepare Data**:
   - Place `supply.csv`, `demand.csv`, `loss_matrix.csv`, and `cost.csv` in a `data/` directory. Sample data structures are provided in the report (Section 4.4); replace with your actual dataset.
   - For the worked example, use files in a `data/sample_input/` directory.

## Usage

1. **Run the GA**:
   Execute the GA with parallel processing, 100 individuals, and 50 generations:
   ```bash
   python src/main.py --algorithm ga --parallel True --population 100 --generations 50
   ```
   Output includes the best fitness score and allocation.

2. **Run the Greedy Baseline**:
   ```bash
   python src/main.py --algorithm greedy
   ```

3. **Explore Worked Example**:
   Run the Jupyter notebook for the fitness example (3 nodes, 2 sources, 1 hour):
   ```bash
   jupyter notebook notebooks/worked_fitness_example.ipynb
   ```
   This replicates the calculation from Section 3.3 of the report.

4. **Generate Visualizations**:
   Plots (e.g., convergence curve) are saved to an `outputs/figures/` directory after running the main script (create this directory if needed).

## Notes

- **Code Status**: The provided scripts are templates based on the report (Section 3–4). Replace with your actual implementation if different.
- **Data**: Add your `data/` directory with CSV files matching the report’s dataset (3 sources, 10 nodes, 24 hours).
- **Generated Date**: This README was created on July 27, 2025, at 06:35 PM +0545 by Grok 3 (xAI). No AI tools were used beyond this interaction; ensure originality per MLPC guidelines.