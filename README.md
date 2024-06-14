# **KNNavigate**

## **Project Title**:
**Scaling Up Nearest Neighbor Search : How Dataset Size and Dimensionality Affect KNN Variants**

## **Professional Description:**

This project investigates the performance trade-offs between efficiency and accuracy in KNN search algorithms. It compares three variants: Naive KNN, LSH, and KD-Tree, analyzing their training and testing time, memory usage, and effectiveness in finding the `K` nearest neighbors for varying dataset sizes (`N`) and dimensionalities (`D`). Through visualization, the project showcases the approximate nature of LSH and KD-Tree and how they might miss some true nearest neighbors in exchange for faster execution. The findings provide valuable insights into choosing the

## **Objective:**

- Evaluate the performance (training/testing time, memory usage) and accuracy of the following KNN variants for nearest neighbor search:
    - `Naive KNN`
    - `Locality-Sensitive Hashing (LSH)`
    - `KD-Tree`

- Analyze the impact of dataset size (`N`) and dimensionality (`D`) on these factors.
- Visually demonstrate the approximate nature of LSH and KD-Tree by comparing the true `K` nearest neighbors with those found by these methods in a 2D dataset.

## **Methodology:**

- **Data Generation:**
    - Create a 2D dataset with varying `N` and `D` values using a random number generator.

- **KNN Implementations:**
    - **Naive KNN:**
        - Compute the distance between the query point and all data points.
        - Maintain a priority queue (min-heap) to store the `K` closest points encountered so far, updating it as needed.
        - Time complexity: `O(N * D)` for distance calculations, `O(K * log K)` for priority queue operations (can be optimized with more efficient data structures).
    - **LSH:**
        - Define appropriate hash functions that map similar points to the same bucket with high probability.
        - Generate multiple hash tables using different hash functions.
        - Query the hash tables and retain points that fall into the same buckets as the query point.
        - Perform a final distance calculation on the remaining points to identify the true `K` nearest neighbors.
        - Time complexity: Amortized constant time for hash lookups, extra distance calculations for non-perfect hash functions.
        - Memory complexity: Linear in `N` (hash tables) and potentially `D` (hash function parameters).
    - **KD-Tree:**
        - Construct a KD-Tree, a recursive binary tree where each node represents a hyperplane splitting the space based on a chosen dimension.
        - Employ a recursive search algorithm to traverse the KD-Tree, traversing only subspaces that could potentially contain the nearest neighbors.
        - Time complexity: `O(log N)` for searching in high dimensions, can be higher for skewed data distributions.
        - Memory complexity: Linear in `N` (tree structure).

- **Performance Evaluation:**
    - Measure training time (building data structures for LSH and KD-Tree) and testing time (finding `K` nearest neighbors) for each KNN variant.
    - Record memory usage for each variant.
    - Analyze the impact of `N` and `D` on these metrics.

- **Visualization:**
    - Generate a 2D plot of the dataset with the query point highlighted.
    - Identify the true `K` nearest neighbors using the naive KNN approach for reference.
    - Show the partitions created by LSH (buckets) and KD-Tree (hyperplane splits) in the 2D space.
    - Mark the points identified by LSH and KD-Tree as their approximate `K` nearest neighbors.
    - Visually compare true neighbors vs. approximate neighbors to illustrate the trade-off between efficiency and accuracy in approximate methods.

**Contribution : *Mrugank Patil & Omkar Rajeev Prabhu***
