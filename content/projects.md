# An Interactive Fractal Visualization in C++

## Overview
This project implements an **interactive visual exploration** of fractals in C++. Due to the nature of fractals, zooming in on a fractal acts closely as a vectorised image.

The primary goal was to integrate and showcase a comprehensive range of **C++ programming concepts and memory management strategies**, while also exploring recursive mathematical patterns in a performant environment.

---

## Objectives
- Visualize complex fractals (Mandelbrot, Julia, and custom sets) using C++.
- Allow **interactive zooming** and **navigation** through fractal space.
- Use **recursive rendering** logic for generating patterns.
- Employ robust **OOP design** and **template programming** for flexibility and performance.

---

## Core Concepts

| Concept                            | How it was applied |
|-----------------------------------|--------------------|
| **C++ Syntax, Variables**         | Strong type definitions and scoped constants for performance and clarity. |
| **Pointers and References**       | Used for managing pixel buffers and color maps with minimal memory footprint. |
| **Dynamic / Stack / Static Memory** | Recursive buffer management with dynamic memory allocation for fractal generation layers. |
| **Functions and Classes**         | Modular structure separating rendering, math, and UI logic. |
| **Polymorphism**                  | Renderers derived from a base `Fractal` class supporting multiple fractal types. |
| **Namespaces**                    | Grouped related modules (e.g., `math::`, `render::`, `ui::`). |
| **Const correctness**             | Enforced immutability across fractal data computation methods. |
| **Robust class design**           | Used copy constructors, move semantics, RAII for safe resource management. |
| **Template functions and classes**| Supported fractal rendering for both `float` and `double` precision. |
| **Standard Template Library (STL)**| Used `std::vector`, `std::map`, `std::unique_ptr` extensively. |
| **Recursion**                     | Core fractal rendering logic was built using recursive function calls. |
| **Exceptions**                    | Handled user input, memory errors, and rendering exceptions safely. |

---

## Features

- **Fractal Types Supported:** Mandelbrot Set, Julia Set, Custom Iterative Formulas.
- **Zoom & Pan:** Mouse-based controls for infinite zooming into fractal space.
- **Resolution Scaling:** Dynamically adjusts rendering resolution for performance.
- **Vector-like Behavior:** Zoom retains crispness due to recursive mathematical definition.

---

## Illustration Example



```cpp
// Example of Iteration logic for Mandelbrot set
bool Mandelbrot::isInSet(double x, double y, int maxIter) const {
    double zx = 0, zy = 0;
    for (int i = 0; i < maxIter; ++i) {
        double temp = zx*zx - zy*zy + x;
        zy = 2*zx*zy + y;
        zx = temp;
        if ((zx*zx + zy*zy) > 4.0) return false;
    }
    return true;
}
