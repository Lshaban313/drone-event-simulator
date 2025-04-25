# Drone Event Simulator

A Python console-based simulator for planning a single UAV’s route on a 2D grid to detect probabilistic events (e.g., wildfires) under time, obstacle, and regulatory constraints. The simulator combines a **greedy high-level planner** (reward-to-cost ratio) with **A\* pathfinding**, and models **probabilistic sensing** on arrival or from neighboring cells.

---

## 📋 Features

- **Custom Grid Layout**  
  - `G` = Free (green)  
  - `O` = No-fly zone (orange)  
  - `R` = Obstacle (red)  
  - `B` = Base (start/return)

- **Probabilistic Events**  
  - Assign any cell a probability `p` of containing an event.  
  - Full detection on-cell (`p`), reduced detection from adjacent cell (`0.9 × p`).

- **Path Planning**  
  - **High-Level (Greedy)**: Selects the next event to visit by maximizing **effective p / cost** (where cost = travel steps + stay time).  
  - **Low-Level (A\*)**: Computes the shortest path around obstacles and no-fly zones.

- **“Stay to Boost” Detection**  
  - Upon arrival, the drone can “stay” multiple time units (up to the point it must return) to make repeated detection attempts, increasing the chance of success.

- **ASCII-Grid Console Output**  
  - Prints an initial and final map with a clear legend.  
  - Overlays event locations (`E`), the drone’s route (`*`), and the base (`B`).

- **Detailed Logging & Metrics**  
  - Route taken, remaining time, detection attempts and results, combined mission success probability.

---

## 🚀 Getting Started

### Prerequisites

- Python **3.7+**  
- No external dependencies (uses only standard library modules: `heapq`, `random`, `time`, etc.)

### Installation

1. **Clone the repository**  
   ```
   git clone https://github.com/<your-username>/drone-event-simulator.git
   cd drone-event-simulator
