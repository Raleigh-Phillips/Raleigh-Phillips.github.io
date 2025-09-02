---
title: "Fractal Visualization"
date: 2025-08-29
summary: "An Interactive Fractal Visualization in C++"
tags: ["Mandelbrot","Julia","C++"]
cover:
  image: "fractal-cover.jpg"    
  alt: "Mandelbrot Set"
  relative: true
  hiddenInList: false
  hiddenInSingle: false
draft: false
---



# An Interactive Fractal Visualization in C++

In the beginning, the primary goal was to integrate and showcase some of the core attributes contained in **C++ programming**, mainly on the memory management side of things. But, also on some more positive things as well.  

So, how can we showcase: 
  - The dubious task of memory management
  - An opportunity to use multi-threading 
  - The performance of C++ 
  - The ability to perpetually work on an application, while maintaining the functionality of features to a user.

Hmm, well Professor Curtis Larsen came up with the brilliant idea of working around fractals. 

So, this project implements an **interactive visual exploration** of fractals in C++. A slight caveat to this creation: zooming in on a fractal acts closely as a vectorised image, producing a seemingly endless display of high resolution. Owed all to the nature of fractals of course.

---

## Formal Objectives:
  - To visualize complex fractals (Mandelbrot and Julia sets) using C++.
  - Produce an ability to **interactively zoom** and **navigate** through fractal space.
  - Implement **recursive rendering** logic to actively generate these patterns.
  - Employ an **OOP design** to allow flexibility and functionality.

---

## Aforementioned Concepts

| Concept                             | Benefit                           | How it was applied |
|-------------------------------------|-----------------------------------|--------------------|
| **C++ Syntax, Variables**           | Performance/Clarity               | Strongly typed definitions along with scoped constants |
| **Pointers and References**         | Minimise footprint on memory      | Used for managing pixel buffers and color maps |
| **Dynamic / Stack / Static Memory** | Memory appropriation              | Dynamic memory for recursive fractal generation |
| **Functions and Classes**           | Modular structure                 | Separating the rendering, math and user options. |
| **Polymorphism**                    | Extendable functionality          | The fractal rendering is derived from a base `Fractal` class and can support the two fractal types | 
| **Namespaces**                      | Associated attribute structure    | Related modules were grouped such as: `ComplexFractal::`, `Image::`, `ActionData::`. |
| **Const correctness**               | Prevents variable mutation        | Used when computing the fractals |
| **Template functions and classes**  | Reusable and generally employable | Produced `float` and `double` precision when rendering fractals. |
| **Standard Template Library (STL)** | Pre-built classes and functions   | Frequently used `std::vector`, `std::istream` and `std::string` |
| **Recursion**                       | Details can be adapted            | Throughout rendering fractals |
| **Exceptions**                      | Error handling                    | Used with things like user input, memory errors and rendering |

---

## Application Features

- **The Fractal Types Supported:** Mandelbrot Set and Julia Set.
- **Zoom & Pan User Controls:** Keypad controls for infinite zooming when exploring fractal space.
- **Colour Gradient:** When a colour is chosen for a fractal, a colour gradient illustrates the fractal density.
- **Vector Resemblance:** When magnifying, the image retains resolution due to the recursive fractal space.
- **Multi-threading** Computes tiles of pixels concurrently for faster rendering

---

## Coding Snippet - Mandelbrot Set Logic



```cpp
// Generating the Mandelbrot set

#include "MandelbrotSet.h"

MandelbrotSet::MandelbrotSet( )
  : ComplexFractal() {
}

MandelbrotSet::MandelbrotSet( const int& height, const int& width, const double& min_x, const double& max_x, const double& min_y, const double& max_y )
  : ComplexFractal(height, width, min_x, max_x, min_y, max_y) {
}

MandelbrotSet::~MandelbrotSet( ) {
}

void MandelbrotSet::calculateNextPoint( const double x0, const double y0, const double& a, const double& b, double& x1, double &y1 ) const{
  x1 = x0*x0 - y0*y0 + a;
  y1 = 2*x0*y0 + b;
}
