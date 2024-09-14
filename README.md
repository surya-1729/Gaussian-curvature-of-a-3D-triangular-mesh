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

Install the dependencies using `pip`:

```bash
pip install numpy meshplot pyglet
pip install git+https://github.com/libigl/libigl-python-bindings@master
```

Make sure you have `Jupyter Notebook` installed. If not, you can install it by:

```bash
pip install notebook
```

## Usage

1. **Download or Clone this Repository**:  
   Download the repository or clone it using:
   ```bash
   git clone https://github.com/your-username/your-repo-name.git
   ```

2. **Run the Jupyter Notebook**:  
   Navigate to the directory containing the notebook file and run the Jupyter Notebook.
   ```bash
   jupyter notebook
   ```
   Open the `gaussian_curvature.ipynb` notebook and execute the cells.

3. **Input Mesh**:  
   The notebook loads a 3D triangular mesh from the file `igea.ply`. Make sure to place your mesh file in the correct path or modify the input file path in the notebook.

4. **Gaussian Curvature Calculation**:  
   The notebook computes Gaussian curvature for each vertex of the mesh. You can modify the script to use different meshes by changing the input file path.

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

## Future Work

- Add support for additional mesh formats.
- Implement other curvature types (e.g., mean curvature).
- Improve computational efficiency for large meshes.

## Contributing

Feel free to submit pull requests or open issues for improvements, bug fixes, or suggestions.

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

---

This README file should give users a clear understanding of how to use the notebook, what it does, and how to set it up. You can further refine it based on additional project details or specific instructions for running the notebook.
