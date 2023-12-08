- Clustering algorithm
- Density based 
- Density based Spatial clustering of application with noise.

## DBSCAN Algorithm Step-by-Step

**DBSCAN stands for Density-Based Spatial Clustering of Applications with Noise.** It is a density-based clustering technique used in machine learning to identify clusters of data points based on their density and proximity to each other. Here's a step-by-step explanation of the DBSCAN algorithm:

**1. Initialize parameters:**

- **Epsilon (ε):** This defines the radius of the neighborhood around a data point. Points within this radius are considered neighbors.
- **MinPts:** This defines the minimum number of neighbors a point needs to be considered a core point.

**2. Core Point, Border Point, and Noise:**

- If the number of data points in the neighborhood is greater than or equal to **ε** the selected point is marked as a core point. Core points are the foundation of clusters.
- If the number of data points in the neighborhood is less than **ε**, but the point is within the neighborhood of another core point, it is marked as a border point.
- If a point is neither a core point nor a border point, it is considered noise.

**2. Start with an unprocessed data point:**

- If the point is not yet processed, it is marked as visited.
- If the point has at least MinPts neighbors within a distance of ε, it is considered a core point.

**3. Expand cluster:**

- If the point is a core point, find all its neighbors within a distance of ε.
- If any of these neighbors are not yet processed, mark them as visited and process them recursively.
- If a neighbor is a core point, expand its cluster by finding its neighbors within ε and repeating the process.
- If a neighbor is border point  add it to current the cluster.
- Continue expanding the cluster until all reachable core points and their neighbors are processed.

**4. Noise:**

- Data points that are not core points and have less than MinPts neighbors are considered noise.
- Noise points are not assigned to any cluster.

**5. Repeat steps 2-4:**

- Continue iterating through unprocessed data points until all points are processed.
- Each iteration might lead to the formation of a new cluster or the assignment of noise points.


**Advantages of DBSCAN:**

- Can identify clusters of arbitrary shapes and sizes.
- Able to handle noise and outliers.
- Relatively computationally efficient.

**Disadvantages of DBSCAN:**

- Sensitive to the choice of epsilon and MinPts parameters.
- Can struggle with high-dimensional data.

