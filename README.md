# 🚑 V2X 5G Emergency Vehicle Coordination System

A comprehensive Vehicle-to-Everything (V2X) based emergency vehicle coordination system integrating **5G network slicing, multi-emergency vehicle (Multi-EV) coordination, reinforcement learning, and intelligent token negotiation** to improve emergency vehicle mobility and traffic management.

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![SUMO](https://img.shields.io/badge/Simulation-SUMO-green)
![License](https://img.shields.io/badge/License-MIT-yellow)
![Status](https://img.shields.io/badge/Project-Research-orange)

---

## 📑 Table of Contents

1. [Overview](#1-overview)
2. [Features](#2-features)
3. [Project Structure](#3-project-structure)
4. [Installation](#4-installation)
5. [Quick Start](#5-quick-start)
6. [Key Performance Metrics](#6-key-performance-metrics)
7. [Use Cases](#7-use-cases)
8. [Expected Performance](#8-expected-performance)
9. [Research Features](#9-research-features)
10. [Documentation](#10-documentation)
11. [Testing](#11-testing)
12. [Contributing](#12-contributing)
13. [License and Authors](#13-license-and-authors)
14. [Acknowledgements](#14-acknowledgements)

---

## 1. Overview

Emergency vehicles such as ambulances and fire trucks often experience delays due to traffic congestion, inefficient lane clearing, and coordination challenges, particularly when multiple emergency vehicles operate simultaneously.

This project explores a **5G-enabled V2X communication framework** that facilitates intelligent emergency vehicle coordination through real-time communication, dedicated network slices, and cooperative traffic management.

The system combines multiple control strategies, including rule-based approaches and Deep Q-Network (DQN) reinforcement learning, to evaluate emergency vehicle coordination and traffic corridor formation.

### 1.1 Key Objectives

- Reduce emergency vehicle travel and clearance time.
- Enable cooperative coordination between multiple emergency vehicles.
- Investigate the role of 5G URLLC network slicing in emergency communication.
- Implement intelligent corridor reservation using token negotiation.
- Compare reinforcement learning, greedy, and cooperative control strategies.
- Evaluate system stability and communication reliability.

---

## 2. Features

### 2.1 Core System

- **5G Network Slicing:** Dedicated URLLC communication slices for emergency vehicles.
- **V2X Communication:** Vehicle-to-Vehicle (V2V) and Vehicle-to-Infrastructure (V2I) communication.
- **Multi-EV Coordination:** Supports coordination between 2–3 simultaneous emergency vehicles.
- **Token Negotiation:** Intelligent corridor token management for resolving conflicts between emergency vehicles.
- **Finite State Machine (FSM):** State-based vehicle behavior with hysteresis for stable transitions.

### 2.2 Control Strategies

| Controller | Description |
|---|---|
| V2X Cooperative Controller | Cooperative traffic coordination using V2X communication and token negotiation. |
| RL DQN Baseline | Deep Q-Network-based reinforcement learning controller. |
| Greedy Reactive Baseline | Rule-based reactive controller used as a baseline. |

### 2.3 Advanced Features

- **Scenario Generator:** Configurable multi-EV scenarios with varying priorities and overlapping routes.
- **Result Export System:** Export experimental metrics in CSV and JSON formats.
- **Visualization System:** Generate analytical plots using Matplotlib and Seaborn.
- **Stability Analysis:** Measure oscillations, corridor integrity, and speed variance.
- **Communication Monitoring:** Evaluate latency, reliability, and message delivery success rates.

---

## 3. Project Structure

```text
V2X-5G/
│
├── src/
│   ├── behavior/
│   │   ├── baseline_greedy.py
│   │   ├── baseline_rl.py
│   │   ├── emergency_controller.py
│   │   ├── fsm.py
│   │   ├── token.py
│   │   ├── negotiation.py
│   │   ├── priority.py
│   │   └── conflict_resolver.py
│   │
│   ├── communication/
│   │   ├── communication_engine.py
│   │   ├── network_slice.py
│   │   ├── slice_manager.py
│   │   └── comms_monitor.py
│   │
│   ├── metrics/
│   │   ├── performance_monitor.py
│   │   └── stability_metrics.py
│   │
│   ├── scenarios.py
│   ├── export.py
│   └── plots.py
│
├── examples/
│   ├── demo_multi_ev.py
│   ├── demo_rl_baseline.py
│   ├── demo_scenarios.py
│   ├── demo_export.py
│   └── demo_plots.py
│
├── scripts/
│   ├── train_rl_baseline.py
│   └── evaluate_rl_baseline.py
│
├── sumo/
├── results/
├── docs/
├── tests/
├── requirements.txt
└── README.md
```

---

## 4. Installation

### 4.1 Prerequisites

Make sure the following software is installed:

- Python 3.8 or higher
- SUMO (Simulation of Urban Mobility)
- Git
- pip package manager

### 4.2 Clone the Repository

```bash
git clone https://github.com/ansh07verma/V2X-5G.git
cd V2X-5G
```

### 4.3 Install Dependencies

```bash
pip install -r requirements.txt
```

### 4.4 Install Optional Dependencies

For the reinforcement learning baseline:

```bash
pip install torch
```

For visualization:

```bash
pip install matplotlib seaborn
```

### 4.5 Install SUMO

**Ubuntu:**

```bash
sudo apt-get install sumo sumo-tools sumo-doc
```

**macOS:**

```bash
brew install sumo
```

**Windows:**

Download and install SUMO from the official website:

https://sumo.dlr.de/docs/Downloads.php

---

## 5. Quick Start

### 5.1 Run Basic Simulation

```bash
python3 src/main.py
```

### 5.2 Generate a Multi-EV Scenario

```python
from src.scenarios import create_scenario

# Generate a scenario with three emergency vehicles
scenario = create_scenario(
    "three_ev_conflict",
    seed=42
)
```

### 5.3 Train the RL Baseline

```bash
python3 scripts/train_rl_baseline.py --episodes 1000
```

### 5.4 Export Simulation Results

```python
from src.export import ResultExporter

exporter = ResultExporter(output_dir="results")

exporter.add_travel_time(
    "ambulance_0",
    0.0,
    125.5,
    3500.0
)

exporter.export_csv(
    run_id="run_001",
    duration=300.0,
    num_emergency_vehicles=1,
    num_regular_vehicles=50
)
```

### 5.5 Visualize Results

```python
from src.plots import (
    plot_multi_ev_clearance,
    load_results
)

results = load_results(
    "results/results_run_001.json"
)

plot_multi_ev_clearance(
    results,
    save_path="plots/clearance.png"
)
```

---

## 6. Key Performance Metrics

The system evaluates performance across three major dimensions.

### 6.1 Performance Metrics

| Metric | Description |
|---|---|
| Travel Time | Total time taken by an emergency vehicle to reach its destination. |
| Clearance Time | Time required to clear a traffic corridor for an emergency vehicle. |
| Success Rate | Percentage of successful corridor formation attempts. |

### 6.2 Stability Metrics

| Metric | Description |
|---|---|
| Oscillation Count | Number of unnecessary lane changes or repeated state transitions. |
| Corridor Integrity | Percentage of time the emergency corridor remains maintained. |
| Speed Variance | Variation in downstream vehicle speeds during coordination. |

### 6.3 Communication Metrics

| Metric | Description |
|---|---|
| Latency | End-to-end communication delay, including average, P95, and P99. |
| Reliability | Successful message delivery rate. |
| Packet Loss | Percentage of communication packets that fail to reach their destination. |

---

## 7. Use Cases

### 7.1 Multi-EV Coordination

Evaluate coordination between multiple emergency vehicles operating simultaneously.

```python
from src.scenarios import ScenarioGenerator

generator = ScenarioGenerator(seed=42)

scenario = generator.generate_scenario(
    num_evs=3,
    overlap_probability=0.8
)
```

### 7.2 Controller Comparison

Compare the performance of different control strategies.

```python
controllers = [
    "greedy",
    "rl_dqn",
    "v2x_cooperative"
]

for controller in controllers:
    results = run_simulation(controller)
    # Analyze simulation results
```

### 7.3 Token Negotiation Analysis

Analyze token negotiation behavior and corridor reservation patterns.

```python
from src.plots import plot_token_negotiation

negotiation_data = extract_negotiation_metrics(results)

plot_token_negotiation(
    negotiation_data,
    save_path="negotiation.png"
)
```

---

## 8. Expected Performance

The following values represent the reported simulation results or performance targets for the three controller approaches. They should be interpreted in the context of the experimental setup.

| Controller | Travel Time | Clearance Time | Oscillations | Success Rate |
|---|---:|---:|---:|---:|
| Greedy Baseline | 150s | 60s | 12 | 70% |
| RL DQN | 130s | 50s | 5 | 85% |
| V2X Cooperative | 110s | 35s | 2 | 98% |

*Note: Performance values should be validated against reproducible simulation runs and experimental configurations before being treated as benchmark results.*

---

## 9. Research Features

### 9.1 Scenario Generation

- Reproducible multi-EV traffic scenarios.
- Configurable vehicle priorities.
- Configurable route overlap probabilities.
- Predefined templates for common emergency traffic scenarios.

### 9.2 Result Export and Experiment Tracking

- CSV export for statistical analysis.
- JSON export for detailed result inspection.
- Experiment metadata support.

### 9.3 Visualization and Analysis

- Multi-EV corridor clearance comparison.
- Stability metric visualization.
- Token negotiation analysis.
- Controller performance comparison.
- Publication-quality figures at 300 DPI.

---

## 10. Documentation

Additional documentation and examples are organized in the project directories.

- **Multi-EV Guide:** Detailed guide for multi-emergency vehicle scenarios.
- **API Documentation:** API and module reference.
- **Examples:** Demonstration scripts for different system features.

---

## 11. Testing

Run the complete test suite:

```bash
python3 -m pytest tests/
```

Run an individual test:

```bash
python3 tests/test_multi_ev.py
```

---

## 12. Contributing

Contributions, suggestions, and improvements are welcome.

To contribute:

1. Fork the repository.
2. Create a feature branch.
3. Implement your changes.
4. Test your implementation.
5. Submit a pull request describing your contribution.

Please follow the existing coding conventions and include relevant tests when introducing new functionality.

---

## 13. License and Authors

This project is distributed under the MIT License. See the [LICENSE](LICENSE) file for details.

**Original Project Author:** Pallav 

This repository should retain applicable original authorship and licensing notices. Additional contributors and modifications can be documented separately.

---

## 14. Acknowledgements

- [SUMO Development Team](https://sumo.dlr.de/)
- V2X research community.
- Research on 5G network slicing and URLLC communication.
- Open-source developers and contributors whose work supports this project.

---

## 📞 Contact and Resources

- [GitHub Repository](https://github.com/ansh07verma/V2X-5G)
- [SUMO Documentation](https://sumo.dlr.de/docs/)
- [5G Network Slicing Research](https://www.3gpp.org/)

---

**Disclaimer:** This is a research-oriented simulation project for investigating V2X-based emergency vehicle coordination using 5G network slicing. The reported performance is simulation-dependent and does not establish real-world deployment readiness. Additional validation, safety assessment, and real-world testing are necessary before practical deployment.
