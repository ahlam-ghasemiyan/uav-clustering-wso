🚁 UAV Clustering using White Shark Optimizer (WSO)
An energy-aware clustering framework for UAV networks powered by the White Shark Optimizer — a bio-inspired metaheuristic algorithm.

https://img.shields.io/badge/Python-3.9%2B-blue?style=for-the-badge&logo=python&logoColor=white
https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white
https://img.shields.io/badge/Status-Research%20Project-orange?style=for-the-badge
https://img.shields.io/badge/License-All%20Rights%20Reserved-red?style=for-the-badge

📖 Overview
This repository implements an energy-efficient clustering scheme for Unmanned Aerial Vehicle (UAV) networks using the White Shark Optimizer (WSO) — a nature-inspired metaheuristic algorithm proposed by Braik et al. (2022).

The algorithm selects an optimal subset of UAVs to act as Cluster Heads (CHs), minimizing a multi-objective fitness function that combines four independent criteria:

Energy efficiency of the network

Cluster node density (to avoid oversized clusters)

Average intra-cluster distance (members → CH)

Average distance from CHs to the Base Station (BS)

The ultimate goal is to prolong network lifetime, balance energy consumption, and reduce communication overhead in UAV-assisted wireless networks.

🔬 Developed as an academic research project on UAV network optimization.

✨ Key Features
🧠 White Shark Optimizer (WSO) — full from-scratch implementation

🎯 Multi-objective fitness function with four weighted criteria

⚙️ Fully configurable via command-line arguments

🔁 Reproducible experiments using random seeds

💾 JSON output for downstream analysis and visualization

📦 Modular architecture — each concern isolated in its own module

🚀 Zero heavy dependencies — only numpy required

🛠 Tech Stack
Component	Purpose
Python 3.9+	Core implementation
NumPy	Vectorized numerical computation
argparse	CLI argument parsing
JSON	Result serialization
📋 Prerequisites
Python 3.9 or higher

pip package manager

🚀 Installation
Clone the repository and install dependencies:

bash
git clone https://github.com/YOUR-USERNAME/uav-clustering-wso.git
cd uav-clustering-wso
pip install -r requirements.txt
requirements.txt
txt
numpy
🎮 Usage
Run the simulation from the project root directory:

bash
python -m clustering.clustering_sim --n 100 --pop 50 --gen 100 --seed 42
Command-line Arguments
Flag	Type	Default	Description
--n	int	100	Number of UAVs to deploy in the field
--pop	int	50	WSO population size
--gen	int	100	Number of generations (iterations)
--seed	int	42	Random seed for reproducibility
Example Runs
Small-scale test:

bash
python -m clustering.clustering_sim --n 50 --pop 20 --gen 50 --seed 1
Large-scale scenario:

bash
python -m clustering.clustering_sim --n 300 --pop 100 --gen 300 --seed 2025
📤 Output
Console Output
text
Best fitness: 12.3456
CH indices: [3, 17, 42, 88]
Result saved to clustering_result.json
JSON Output (clustering_result.json)
json
{
  "best_fitness": 12.3456,
  "ch_indices": [3, 17, 42, 88],
  "clusters": {
    "3": [0, 1, 2, 5, 8, ...],
    "17": [12, 14, 15, ...],
    "42": [...],
    "88": [...]
  }
}
Field	Description
best_fitness	Final value of the objective function
ch_indices	Indices of UAVs selected as Cluster Heads
clusters	Mapping from each CH index to its list of member UAV indices
🧩 Fitness Function

Criteria Breakdown
Symbol	Criterion	Rationale	Desired
f₁	Energy efficiency	Favors networks with optimal CH ratio	Maximize
f₂	Cluster node density	Penalizes oversized clusters	Minimize
f₃	Avg. distance (member → CH)	Reduces intra-cluster transmission cost	Minimize
f₄	Avg. distance (CH → BS)	Reduces long-range transmission cost	Minimize


🧬 Algorithm Overview — White Shark Optimizer
The White Shark Optimizer (WSO) mimics the hunting strategy of great white sharks, which rely on:

Speed and agility — rapid movement toward prey

Sensory perception — detecting prey through smell and hearing

Social behavior — hunting in coordinated groups

Key WSO Phases
Phase	Behavior	Purpose
Exploration	Movement toward optimal prey positions	Global search
Exploitation	Refined movement near best solutions	Local search
Fish school	Following best-known positions	Information sharing
Behavioral switch	Adaptive transition between phases	Balance exploration/exploitation
Application to UAV Clustering
In this project, each shark in the population represents a candidate set of Cluster Heads. The optimizer iteratively refines this set to minimize the composite fitness function.

📁 Project Structure
text
uav-clustering-wso/
├── clustering/
│   ├── __init__.py            # Package initializer
│   ├── clustering_sim.py      # Main entry point (CLI)
│   ├── fitness.py             # Fitness functions (f1, f2, f3, f4, objective_F)
│   ├── utils.py               # Helper utilities (UAV generation, distance, etc.)
│   └── wso.py                 # White Shark Optimizer implementation
├── requirements.txt           # Python dependencies
├── README.md                  # This file
├── LICENSE                    # License file
├── .gitignore                 # Git ignore rules
└── screenshots/
    └── demo.png               # Simulation preview
Module Responsibilities
Module	Role
clustering_sim.py	CLI parsing, orchestration, output serialization
fitness.py	Objective function and its four components
utils.py	UAV generation, Euclidean distance, helper routines
wso.py	Full implementation of the White Shark Optimizer
🔬 Reproducibility
All experiments are fully reproducible:

The random seed is explicitly passed to both UAV generation and WSO initialization.

Given the same --n, --pop, --gen, and --seed, the output is deterministic.

For paper-quality results, run the same configuration with multiple seeds and average the outcomes:

bash
for seed in 1 2 3 4 5 42 100 2025; do
    python -m clustering.clustering_sim --n 100 --pop 50 --gen 100 --seed $seed
    mv clustering_result.json "results/run_$seed.json"
done
🎯 Use Cases
📡 UAV-assisted wireless sensor networks

🛰️ Drone swarm coordination

📶 Disaster response communication networks

🏙️ Smart city aerial infrastructure

🎓 Metaheuristic algorithm benchmarking

📜 License
All Rights Reserved.

Copyright (c) 2025 Eng. Ghasemian

This project and its source code are the exclusive property of the author.
No part of this project may be copied, modified, distributed, sublicensed,
or used in any form — commercial or non-commercial — without the explicit
written permission of the author.

This project is intended solely for personal and educational purposes as
part of an academic research study on UAV clustering using the White Shark
Optimizer (WSO) algorithm.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHOR BE LIABLE FOR ANY CLAIM, DAMAGES, OR OTHER LIABILITY ARISING FROM, OUT
OF, OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

👨‍🏫 Author
Engineer Ahlam Ghasemiyan
Developed as part of an academic research project on UAV network optimization and metaheuristic algorithms.

📚 References
Braik, M., Hammouri, A., Atwan, J., Al-Betar, M. A., & Awadallah, M. A. (2022).
White Shark Optimizer: A novel bio-inspired meta-heuristic algorithm for global optimization problems.
Knowledge-Based Systems, 243, 108457.
DOI: 10.1016/j.knosys.2022.108457

Related literature on UAV clustering, energy-aware routing, and cluster head selection in wireless networks.

🙏 Acknowledgements
Inspired by the original WSO paper.

Built with NumPy for efficient numerical computation.

Thanks to the open-source research community.

⚠️ Note: This project is intended for academic and educational use only.
All trademarks and referenced works belong to their respective owners.

