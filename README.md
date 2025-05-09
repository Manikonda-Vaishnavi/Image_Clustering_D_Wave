# Clustering with D-Wave Quantum Computer
This repository demonstrates how to identify clusters in a data set using the D-Wave quantum computer.
Clustering is a powerful technique for extracting insights from unlabeled data, such as housing data or consumer behavior.

# Overview
When dealing with large data sets, we often encounter unlabeled data. Clustering allows us to group similar data points,
providing insights even without labels. For example, in housing data, clusters may indicate different neighborhoods based
on square footage and price. Similarly, clustering consumer behavior data can help identify demographics.

# Key Features
Identify Clusters: Group data points based on similarities.
Quantum Computing: Utilize D-Wave's quantum annealing for clustering.
Visualization: Visualize the clustering results and the problem formulation.
Usage
To run the demo with a simple, hardcoded data set:

bash
Run
Copy code
python clustering.py
To run the demo with a more sophisticated data set and visualization:

bash
Run
Copy code
python example_clusters.py
This will provide a visualization of the clustering problem on the D-Wave problem inspector, along with plots
of the original data set and its clustering solution.

# Code Overview
The D-Wave quantum computer accepts problems formulated in Binary Quadratic Model (BQM) format.
The goal is to build a BQM that represents our clustering problem, ensuring that a low-energy solution corresponds
to a valid clustering.

# Key Properties of Clustering
Single Cluster Membership: Each data point can only belong to one cluster.
Proximity Clustering: Data points that are close together should belong to the same cluster.
Separation of Distant Points: Data points that are far apart should belong to different clusters.

# Implementation Details
Single Cluster Membership: Each data point is represented by three nodes corresponding to three clusters
(red, green, blue). The valid states for cluster membership are defined as:

python
1 lines
Click to expand
choose_one_group = {(0, 0, 1), (0, 1, 0), (1, 0, 0)}
Proximity Clustering: We assign negative weights to encourage clustering of nearby points using a cosine function:

python
1 lines
Click to expand
weight = -math.cos(d * math.pi)
Separation of Distant Points: We assign negative weights to discourage far-apart points from being in the same
cluster using the hyperbolic tangent function:

python
1 lines
Click to expand
weight = -math.tanh(d) * 0.1
Image Compression Example
This repository also includes an implementation for image compression using quantum annealing. The code loads 
an image, preprocesses it, and applies K-means clustering using a QUBO matrix.


# Load and preprocess the image
def load_image(image_path, resize_shape=(64, 64)):
...
Requirements
Python 3.x
D-Wave Ocean SDK
OpenCV
Scikit-learn
NumPy

# Conclusion
This repository provides a comprehensive demonstration of clustering using the D-Wave quantum computer, along
with an example of image compression. By leveraging quantum computing, we can effectively solve clustering problems
in large, unlabeled data sets.
