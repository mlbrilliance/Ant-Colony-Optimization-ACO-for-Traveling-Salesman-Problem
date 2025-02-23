# Ant Colony Optimization (ACO) for Traveling Salesman Problem

## Developer
Nick Sudh

## Overview
This project implements an Ant Colony Optimization (ACO) algorithm to solve the Traveling Salesman Problem (TSP). The implementation includes visualization tools to help understand the solution process and final results.

## Problem Description
The Traveling Salesman Problem (TSP) is a classic optimization problem where the goal is to find the shortest possible route that visits each city exactly once and returns to the starting city. This implementation uses ACO, a nature-inspired algorithm that mimics how ants find optimal paths using pheromone trails.

## Features
- ACO implementation with configurable parameters
- Real-time visualization of the best route
- Convergence history plotting
- City coordinate visualization with route mapping
- Customizable number of cities and their coordinates

## Implementation Details

### Core Components

1. **Distance Calculation** (`distance` function)
   - Uses Euclidean distance between cities
   - Implemented using NumPy's `linalg.norm`

2. **Route Selection** (`select_next_city` function)
   - Implements roulette wheel selection
   - Probabilistically selects next cities based on pheromone levels and distances

3. **Main ACO Algorithm** (`solve_tsp_with_aco` function)
   - Parameters:
     - `num_ants`: Number of ants in the colony
     - `num_iterations`: Number of iterations to run
     - `alpha`: Influence of pheromone trails (default: 1.0)
     - `beta`: Influence of distances (default: 5.0)
     - `rho`: Pheromone evaporation rate (default: 0.5)
   
   - Process:
     1. Initializes pheromone trails
     2. For each iteration:
        - Each ant constructs a route
        - Updates best route if better solution found
        - Evaporates existing pheromone
        - Deposits new pheromone based on route quality

4. **Visualization** (`plot_route` function)
   - Plots cities as red points
   - Shows route connections in blue
   - Labels each city
   - Includes grid for better readability

### Understanding the Output

1. **Console Output**
   ```
   Best Route: [0, 2, 4, 3, 1]
   Best Distance: 22.35
   ```
   - `Best Route`: Sequence of city indices showing the optimal path found
   - `Best Distance`: Total distance of the best route

2. **Visualization Plots**
   - **Route Plot**:
     - Red dots: City locations
     - Blue lines: Path between cities
     - Numbers: City indices
     - Title: Shows the total distance of the route
   
   - **Convergence History**:
     - X-axis: Iteration number
     - Y-axis: Best distance found so far
     - Shows how solution quality improves over time

## Dependencies
Required Python packages (specified in `requirements.txt`):
```
numpy>=1.21.0
matplotlib>=3.4.0
```

## Installation
1. Clone the repository
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage
Run the main script:
```bash
python aco_tsp.py
```

### Customizing Parameters
You can modify the following parameters in the `main()` function:
```python
best_route, best_distance, history = solve_tsp_with_aco(
    cities,
    num_ants=10,          # Increase for more exploration
    num_iterations=100,    # Increase for better solutions
    alpha=1.0,            # Pheromone influence
    beta=5.0,             # Distance influence
    rho=0.5              # Evaporation rate
)
```

### Adding Custom Cities
Modify the `cities` array in `main()`:
```python
cities = np.array([
    [0, 0],    # City 0
    [1, 5],    # City 1
    [5, 2],    # City 2
    # Add more cities as needed
])
```

## How to Interpret Results

1. **Route Quality**
   - Lower total distance indicates a better solution
   - The algorithm may find different solutions on different runs due to its probabilistic nature

2. **Convergence Plot**
   - A steep initial decline indicates rapid improvement
   - Flattening of the curve suggests convergence
   - If the curve doesn't flatten, consider increasing iterations

3. **Route Visualization**
   - Shows the physical path taken
   - Helps identify if the solution makes intuitive sense
   - Can help spot potential areas for improvement

## Tips for Better Results
1. Increase `num_ants` for more thorough exploration
2. Increase `num_iterations` for better solution quality
3. Adjust `alpha` and `beta` to balance between:
   - Following existing good paths (higher `alpha`)
   - Exploring new possibilities (higher `beta`)
4. Modify `rho` to control how quickly old paths are forgotten

## License
This project is open source and available under the MIT License.

