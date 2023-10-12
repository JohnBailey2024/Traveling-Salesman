# Traveling-Salesman

## Overview

This project presents a novel approach to solving the Traveling Salesman Problem (TSP) using a combination of K-Nearest Neighbors (KNN) and Ant Colony Optimization (ACO). The TSP is a classic combinatorial optimization problem that seeks the shortest possible route to visit a set of cities and return to the starting city.

## Problem Statement

The TSP is known for its high computational complexity, making it a challenging problem to solve. The objective is to find an optimal route that minimizes the total distance traveled while visiting each city exactly once.

## Solution Strategy

In order to effectively visit all 115,475 cities in a computationally efficient manner I chose to use K-means clustering to split the cities into 1000 smaller clusters then find the shortest route between each cluster using KNN and the shortest route inside each cluster using Ant Colony Optimization.

### K-Nearest Neighbors (KNN)

We begin by employing the K-Nearest Neighbors algorithm to find the shortest distance between each of the 1000 clusters. KNN is a straightforward heuristic that constructs a tour by iteratively selecting the nearest unvisited city from the current city. It serves as a fast way of finding the shortest route between clusters.

### Ant Colony Optimization (ACO)

ACO is a nature-inspired metaheuristic that models the behavior of ants in finding the shortest path. Ants build solutions incrementally, leaving pheromone trails that guide their choices. Over time, ACO converges toward an optimal or near-optimal solution. The issue with Ant Colony Optimization is how computationally intensive it is. As such it would be nearly impossible to run ACO on the entire dataset, but it was able to find a near-optimal solution inside each of the 1000 clusters

### Key Steps in Our Approach

1. **Data Preparation**: We load the initial dataset, which includes all of the city coordinates.

2. **K-Means Clustering**: We cluster all 115,475 cities into 1000 clusters of roughly equal number. 

3. **K-Nearest Neighbors (KNN)**: We use KNN to generate an initial tour between each of the 1000 clusters.

4. **Ant Colony Optimization (ACO)**: Run ACO inside each cluster, calculating the total distance and continually adding it to a list.

5. **Result Evaluation**: We evaluate the final solution's quality, and compare it to a function that calculates the total distance based on the order the coordinates appear in the csv file.

## Key Benefits

Our approach combines the efficiency of KNN for a quick route between clusters with the global optimization power of ACO in each cluster. This results in a high-quality solution while still being computationally feasible for larger TSP instances.


