# CPlusPlus-Gauss-Kronrod-3D-Integrator
Multidimensional numerical integration in C++ using Gauss–Legendre and Gauss–Kronrod quadrature rules.
## Overview
This program implements a highly flexible 3D quadrature integrator that supports both Gauss-Kronrod and Gauss-Legendre rules. It is designed to handle extremely high precision by supporting Kronrod grids from 15 up to 1,023 points (and Legendre from 7 up to 511 points).
## Features
- Three-Dimensional Integration: Performs numerical integration of functions over a 3D cuboidal domain using either Gauss-Kronrod or Gauss-Legendre quadrature.
- Systematically Increasing Precision: Supports Kronrod grid sizes from 15 up to 1,023 points, and matching Gauss-Legendre grids from 7 up to 511 points, allowing controlled balancing between speed and precision.
- Flexible Integrand Selection: Users can specify any function as the integrand by modifying a single routine in the code, making the integrator adaptable to a wide range of problems.
- Highly Customizable Domains: Integration boundaries for all three axes (x,y, and z) are easily adjustable by modifying a few parameters.
- Efficient Memory Organization: Pre-allocated arrays and pointers for roots and weights enable fast switching and minimal overhead for multiple quadrature orders.
- Extensible to Higher Dimensions: The structure is written for 3D but designed so you can further extend the code to higher dimensions with nested loops and additional root/weight arrays.
- Adjustable Tolerance for Precision: The integrator allows you to set an error tolerance parameter that controls the precision of the integration. By lowering this tolerance value, you can obtain higher accuracy results at the cost of increased computational effort.
## Requirements
- C++ Compiler: A modern C++ compiler with support for C++17 or later (e.g., GCC 7+, Clang 5+, MSVC 2017+).
- Standard Library Only: This project uses only the C++ standard library, with no external dependencies, ensuring easy compilation and portability.

## Usage
- Clone or download this repository.
- Modify the Integrand Function: Open the file GK_GL_3D_QUAD.cpp in your text editor or IDE and locate the function where the integrand is defined. Edit this function to specify the mathematical function you want to integrate over 3D.
- Set Integration Limits and Tolerance: Adjust integration limits for x, y, and z and specify the desired error tolerance parameter in the code.
- Build the project:
  ```
  g++ -std=c++17 -O2 GK_GL_3D_QUAD.cpp -o GK_GL_3D_QUAD
  ```
- Run the Executable:
 ```
 ./GK_GL_3D_QUAD
 ```
- Automatic Order Refinement: The integrator systematically increases the quadrature order—from the lowest Kronrod point set (15 points) up to the maximum (1,023 points)—automatically refining the precision until the requested tolerance (error threshold) is met.
- View Results: The output will provide the computed integral values with corresponding estimated precision and timing information.

## Example Output
 ```
 The function didn't converge with 15 points. Moving to the next order.
starting order Npt_gk=31
The function converged with 31 points giving 7.4728303145e-01!
ans=7.4728303145e-01
Done calculating f(x)

Process returned 0 (0x0)   execution time : 0.149 s
Press any key to continue.
```
## Performance Characteristics

- Deterministic quadrature refinement from 15 to 1023 Kronrod nodes.
- Runtime scales predictably with quadrature order and dimensional nesting.
- Pre-allocated arrays minimize dynamic memory overhead.
- Compiled with -O2 optimization for performance benchmarking.
- Execution time printed for each run for direct performance evaluation.
## Numerical Stability & Error Control

- Automatic order escalation until user-defined tolerance is satisfied.
- Explicit error threshold parameter enables precision-speed tradeoff.
- High-order Kronrod grids ensure stable integration of stiff functions.
- Deterministic convergence behavior compared to Monte Carlo variance.
## Quantitative Modeling Relevance

High-precision multidimensional integration is fundamental in:

- Expectation estimation in stochastic systems
- Risk metric evaluation
- Probabilistic model calibration
- Deterministic alternatives to Monte Carlo sampling

This project demonstrates structured error control, adaptive precision refinement, and performance-aware numerical implementation in C++. 
## License
This project is released under the MIT License. See the LICENSE file for details.
