# 5G-Based-Vehicle-to-Everything-V2X-Emergency-Coordination-System

## Overview

A comprehensive V2X-based emergency vehicle coordination system using 5G network slicing, multi-EV support, reinforcement learning, and intelligent token negotiation.

## Features
1. Core System
```text
-5G Network Slicing: Dedicated URLLC slices for emergency vehicles.
-V2X Communication: Real-time vehicle-to-vehicle and vehicle-to-infrastructure communication.
-Multi-EV Coordination: Support for 2-3 simultaneous emergency vehicles with priority-based conflict resolution.
-Token Negotiation: Intelligent corridor token management for multi-EV scenarios.
-FSM with Hysteresis: Stable state transitions for vehicle behavior.
```
2. Controllers
-V2X Cooperative Controller: Full V2X coordination with token negotiation.
-RL DQN Baseline: Deep Q-Network reinforcement learning baseline.
-Greedy Reactive Baseline: Simple reactive baseline for comparison.

3. Advanced Features
-Scenario Generator: Create multi-EV scenarios with configurable priorities and overlapping routes.
-Result Export System: Export metrics to CSV/JSON for analysis.
-Visualization System: Publication-quality plots using Matplotlib/Seaborn.
-Stability Metrics: Track oscillations, corridor integrity, and speed variance.
-Communication Monitoring: Track latency, reliability, and message success rates.

## Tech Stack

- Programming Language:
- Framework:
- Libraries:
- Tools:

## Architecture



## Project Structure
```text
V2x5G/
├── src/
│   ├── behavior/           # Vehicle behavior controllers
│   │   ├── baseline_greedy.py      # Greedy reactive baseline
│   │   ├── baseline_rl.py          # RL DQN baseline
│   │   ├── emergency_controller.py # V2X cooperative controller
│   │   ├── fsm.py                  # Finite state machine
│   │   ├── token.py                # Token management
│   │   ├── negotiation.py          # Token negotiation
│   │   ├── priority.py             # Priority rules
│   │   └── conflict_resolver.py    # Conflict resolution
│   ├── communication/      # 5G communication
│   │   ├── communication_engine.py # V2X communication
│   │   ├── network_slice.py        # Network slicing
│   │   ├── slice_manager.py        # Slice management
│   │   └── comms_monitor.py        # Communication monitoring
│   ├── metrics/            # Performance metrics
│   │   ├── performance_monitor.py  # Performance tracking
│   │   └── stability_metrics.py    # Stability tracking
│   ├── scenarios.py        # Scenario generator
│   ├── export.py           # Result export system
│   └── plots.py            # Visualization system
├── examples/               # Demo scripts
│   ├── demo_multi_ev.py
│   ├── demo_rl_baseline.py
│   ├── demo_scenarios.py
│   ├── demo_export.py
│   └── demo_plots.py
├── scripts/                # Training/evaluation scripts
│   ├── train_rl_baseline.py
│   └── evaluate_rl_baseline.py
├── sumo/                   # SUMO configuration
├── results/                # Simulation results
└── docs/                   # Documentation
```
## Installation

1. Prerequisites
Python 3.8+
SUMO (Simulation of Urban MObility)
Git
Setup
Clone the repository

git clone https://github.com/ansh07verma/V2X-5G.git
cd V2X-5G
Install dependencies

pip install -r requirements.txt
Install optional dependencies

# For RL baseline
pip install torch

# For visualization
pip install matplotlib seaborn
Install SUMO

macOS: brew install sumo
Ubuntu: sudo apt-get install sumo sumo-tools sumo-doc
Windows: Download from the SUMO website



### Setup



Install dependencies:

```bash
# Add appropriate installation command
```

## Usage

Explain how to run the project.

```bash
# Add execution command
```

## Results / Demonstration

Add screenshots, simulation results, benchmarks, or demo links.

## Future Improvements

- Improvement 1
- Improvement 2
- Improvement 3

## Acknowledgements

Mention relevant references, resources, and original project contributors where applicable.

## License

Specify the project's license.
