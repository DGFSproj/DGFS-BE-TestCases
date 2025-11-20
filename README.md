# DGFS Test Cases
This repository contains test cases in normal shock flow, Couette flow, 2D pressure-driven flow in microchannel for the DGFS Full Boltzmann solver. The solver can be found in the following repository https://github.com/DGFSproj/DGFS-BE-Solver


## Example: Running Couette Flow Case

This example demonstrates how to run a 2D Couette flow simulation using the DGFS-BE solver.

### 1. Download Required Files

Obtain the following files:
- `dgfs_2d_couette.geo` — GMSH geometry and mesh definition file
- `dgfs_2d_couette.ini` — DGFS configuration file (contains solver settings, initial/boundary conditions, etc.)

### 2. Generate the Mesh

Use GMSH to generate a `.msh` mesh file from the `.geo` definition:

```bash
gmsh -2 dgfs_2d_couette.geo
```

This will produce `dgfs_2d_couette.msh`.

### 3. Convert to DGFS Mesh Format

Convert the GMSH mesh to DGFS-native `.frfsm` format:

```bash
frfs import dgfs_2d_couette.msh mesh.frfsm
```

(Optional) To visualize the mesh:

```bash
gmsh dgfs_2d_couette.msh
```

### 4. Run the Simulation

Execute the solver using CUDA backend:

```bash
frfs run mesh.frfsm dgfs_2d_couette.ini -b cuda
```

This will produce solution output files with the `.frfss` extension inside the case directory, one for each saved timestep.

### 5. Post-Processing: Convert to VTU Format

To convert `.frfss` files into `.vtu` format for visualization:

```bash
frfs export mesh.frfsm bulksol_dgfs_2d_couette-10.0.frfss bulksol_dgfs_2d_couette-10.0.frfss.vtu -d 16
```

- `-d 16` means that each DG element is subdivided into 16 sub-elements for smoother visualization
- The output `.vtu` file can be visualized with ParaView or Tecplot
  
![VTU Conversion Diagram](/Solution_generation.png)

To visualize using Tecplot:

```bash
tec360 bulksol_dgfs_2d_couette-10.0.frfss.vtu
```

### 6. Resources about creating .geo and .msh file
https://freshkiss3d.gitlabpages.inria.fr/freshkiss3d/auto_examples_mesh/example_generate_mesh.html

http://www.manpagez.com/info/gmsh/gmsh-2.2.6/gmsh_47.php

https://www.manpagez.com/info/gmsh/gmsh-2.4.0/gmsh_69.php

https://openfoamwiki.net/index.php/2D_Mesh_Tutorial_using_GMSH

https://chi-tech.github.io/d4/db9/_gmsh_example_01.html

https://gmsh.info/doc/texinfo/gmsh.html

