# Gaussian Curvature of 3D Triangular Mesh - Jupyter Notebook

## Overview

This project calculates the **vertex-wise Gaussian curvature** of a 3D triangular mesh using Python and is presented in the form of a Jupyter Notebook. Gaussian curvature helps in understanding the local shape of a surface, such as whether a surface region is convex or concave.

The notebook reads point cloud data in the form of a triangular mesh and calculates Gaussian curvature at each vertex.

## Features

- **Mesh Loading**: Uses `libigl` for reading the triangular mesh.
- **Mesh Visualization**: Utilizes `meshplot` to visualize the mesh and curvature.
- **Custom Curvature Calculation**: The notebook contains a custom implementation for Gaussian curvature calculation without using external curvature functions.
- **Color Mapping**: Gaussian curvature values are visualized with a colormap applied to the mesh surface.

## Requirements

To run the notebook, you need to install the following dependencies:

- Python 3.x
- Required libraries:
  - `igl` (for mesh processing)
  - `meshplot` (for 3D visualization)
  - `numpy` (for mathematical operations)

## Gaussian Curvature Calculation Algorithm

The algorithm iterates through each triangle in the mesh and computes the internal angles at each vertex using the cosine rule. Then, it calculates the corresponding Gaussian curvature values for each vertex based on the angular deficits and the areas of the surrounding triangles.

### Key Steps in the Algorithm:

1. **Side Lengths Calculation**:  
   The lengths of the sides of the triangle are calculated using the Euclidean distance formula.

2. **Angle Calculation**:  
   Internal angles at each vertex are computed using the cosine rule.

3. **Area Calculation**:  
   The area of each triangle is calculated using the sine of one of its angles and the lengths of the sides.

4. **Curvature Calculation**:  
   The Gaussian curvature at each vertex is calculated as:
   \[
   K = \frac{2\pi - \text{sum of angles at vertex}}{\text{area of surrounding triangles}}
   \]

## File Structure

```
├── gaussian_curvature.ipynb  # Jupyter notebook with the curvature calculation
├── igea.ply                  # Sample 3D triangular mesh (make sure this is in the same directory)
├── README.md                 # This readme file
```

## Visualization

The Gaussian curvature is visualized using `meshplot` by mapping the curvature values to a color scale. The notebook contains a function that plots the mesh and colors each vertex based on its Gaussian curvature value.

Example color mapping visualization:
```python
colors = mp.utils.get_colors(g, colormap='viridis', normalize=False, vmin=-200, vmax=200)
mp.plot(vert, tri, colors)
```

