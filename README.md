# Autonomous Multi-Agent Vacuum Simulation (NetLogo)

## Executive Summary
This project implements a **Multi-Agent System (MAS)** simulating a fleet of autonomous vacuum cleaners operating within a dynamic 2D environment. Developed in **NetLogo**, the simulation serves as a practical study of **Rational Agents**, exploring core AI concepts such as **Reactive Architecture**, **Resource Management**, **Spatial Perception**, and **Cooperative Intelligence**.

The system contrasts two distinct architectural approaches—a standalone rational model versus a communicative, cooperative model—to analyze the impact of information sharing on global system efficiency.

## Environment & Topology
The simulation runs on a **closed, non-toroidal grid**, where agents must navigate semantic constraints defined by specific patch properties:
* **Agent Interaction:** Agents must avoid collisions with static obstacles (Walls) and dynamic entities (Other Agents).
* **Resource Management:** Agents monitor distinct internal states (Energy Level, Debris Capacity).
* **Designated Zones:** The map includes specific coordinates for **Charging Stations** (Blue) and **Waste Disposal Sites** (Green).

## Agent Architectures

### 1. Base Model (Reactive & Rational)
The fundamental implementation of a goal-based agent.
* **Behavior:** Follows a strict Finite State Machine (FSM) for movement, cleaning, and seeking energy.
* **Limitations:** Operates with **Limited Memory** (stores only the last known charger/deposit) and zero communication.
* **Navigation:** Uses randomized rotation heuristics for obstacle avoidance.

### 2. Enhanced Model (Cooperative & Adaptive)
An evolution of the base model introducing **Swarm Intelligence** principles.
* **Knowledge Sharing:** Agents exchange topological data (coordinates of chargers/deposits) when in proximity (`InfoNeighbour`).
* **Extended Memory:** Capable of mapping and storing multiple points of interest.
* **Complex Environment Handling:** Adapts to "High Density Debris" (Yellow patches) which require varied processing time.
* **Lifecycle Mechanics:** Implements **Reproduction** logic and simulated **Hardware Degradation** (sensor failure after N cycles).

## Algorithmic Implementation

### Core Functions
* `Setup`: Procedural generation of the environment (stochastic distribution of dirt and obstacles).
* `MoveAspiradores`: The primary **Action Loop** executing the perception-action cycle.
* `InfoNeighbour`: Handles the peer-to-peer data exchange protocol.
* `MemorizaCarregador/Lixo`: Updates the agent's internal spatial map.
* `AheadWhite`: Collision avoidance logic using look-ahead sensors.

### Simulation Parameters
The system features a comprehensive **Control Dashboard** allowing real-time tuning of:
* **Environmental Variables:** Obstacle density (`nPatchesBranco`), Dirt distribution (`percentagemVermelho`).
* **Agent Specs:** Battery capacity, Carrying payload, and Vision range.
* **Heuristics:** Thresholds for "Power-Saving Mode" and cleaning duration.

## Experimental Analysis
The performance of both models was validated through **iterative testing (N=10 per scenario)**. Key metrics analyzed include:
* **Time-to-Completion:** Ticks required to reach 100% cleanliness.
* **Survivability:** Rate of agents that successfully recharged vs. those that depleted energy.
* **Efficiency:** Impact of communication on pathfinding optimization.

*Detailed statistical results and comparative graphs are available in the attached Excel dataset.*

## Visualizations

### Base Model
*Basic rational behavior with independent navigation.*
[Insert Screenshot of Base Model]

### Improved Model
*Visualizing cooperative clusters and handling of high-density debris zones.*
[Insert Screenshot of Improved Model]

---

## Academic Context
This project was developed for the **"Introduction to Artificial Intelligence"** course (2024/2025).

**Team Size:** 2 Members
**Final Evaluation:** 10 / 10
