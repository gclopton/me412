

## OUTLINE

* Numerical methods-introduction
* Error minimization principle \{self reading additional notes\}
* Strong and weak form of PDEs
* Numerical methods to solve PDEs
* Numerical Analysis-General steps

Numerical methods: Mathematical algorithms and computational techniques that are used to find approximate, yet accurate, solutions to complex mathematical problems that are often analytically unsolvabable or too time-consuming.

- complex mathematical problems are thermo-fluidic problems governed by $2^{\text {nd }}$ order PDE is the focus of this course
- Since, these are approximation methods, there would be inherent error associated with them and they can never give exact/analytical solution of the physical problem.
- Therefore, to have accurate numerical predictions close to the exact or analytical solution, the error associated with the numerical methods needs to minimized
- Thus, error minimization is a key principle in developing appropriate numerical method for a given problem
- Error minimization is achieved by considering variations for which calculus of variations is employed.

Discuss: Error minimization

Discuss: Strong form and Weak form

## Numerical Methods to solve Thermo-fluidics problems

1. Finite Difference Method
2. Finite Volume Method
3. Finite Element Method
4. Lattice Boltzmann Method
5. Boundary Element Method
6. Spectral Method
7. Meshless/Mech-free Method
8. And more...

## Numerical Analysis - General procedure

Core idea $=$ Discretization i.e. dividing the domain into discrete number of points and finding solution at each of these points.

Discussion: - Assume solving fluid flow or heat transfer problem in complex geometry

- Therefore, the solution would require solving PDEs or transport equation in some form or other. in this complex
![](https://cdn.mathpix.com/cropped/95b5cecb-0a61-472e-a9f6-2a8064ce0615-2.jpg?height=274&width=317&top_left_y=855&top_left_x=1233)
geometry / domain.
- Finding the numerical solution of the goverining PDE requires:

1. Divide/Discretize the domain into a of discrete sub-domains (control volumes, cells, elements...)
2. Each sub-domain is represented by a set of discrete points (grid points, nodes.)
![](https://cdn.mathpix.com/cropped/95b5cecb-0a61-472e-a9f6-2a8064ce0615-2.jpg?height=261&width=294&top_left_y=1327&top_left_x=1109)
3. Convert the governing PDE into system of algebraic equation valid at each of these polnts using methods like FDM, FVM, FEM...
4. Solve the system of algebraic equation to find the solution at each discrete point.
General philosophy: Losing the continuous nature of the solution of the PDE and obtain the solution at discrete points by solving a system of algebraic equations.

## CFD or Numerical Analysic (Broad steps)

1. Pre-processing:

- Set up the geometry, do meshing and set up the discretized equations
- input data like material properties and other parometers
- Initial condition
- Boundary condition

2. Processing (solution)

- Solve the set of algebrate equations

3. Post-Processing

- Visualize the results (check the accuracy)

