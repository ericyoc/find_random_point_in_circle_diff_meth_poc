# Finding Random Points in a Circle: Comparison of Methods

This project compares four different methods for generating uniformly distributed random points within a unit circle. Each method is implemented in Python, visualized, and analyzed for performance.

## Motivation
The BEST Way to Find a Random Point in a Circle YouTube found at https://www.youtube.com/watch?v=4y_nmpv-9lI

Sources used:
1. https://stackoverflow.com/questions/5837572/generate-a-random-point-within-a-circle-uniformly
3. https://onlinelibrary.wiley.com/doi/10.1155/2017/3571419#derivation-of-the-irwin-hall-distribution
4. https://programming.guide/random-point-within-circle.html#google_vignette

Chapters:
0:00 Introduction
0:23 Rejection Sampling
2:59 Coordinate Systems
4:59 Inverse Transform Sampling
10:34 Infinite Triangle Sampling
12:49 random() + random() vs random() * 2
13:59 Irwin-Hall Distribution
16:17 max(random(), random())
17:37 Conclusion

## Methods

### 1. Rejection Sampling

![Rejection Sampling Points](https://github.com/ericyoc/find_random_point_in_circle_diff_meth_poc/raw/main/circle_method_visualizations/Rejection_Sampling_points.jpg)

**How it works:**
1. Generate random (x, y) coordinates in the range [-1, 1].
2. Keep the point if x^2 + y^2 <= 1, otherwise reject and try again.

**Pros:** Simple to implement and understand.
**Cons:** Can be inefficient, especially for higher dimensions, as it discards points.

### 2. Maximum Method

![Maximum Method Points](https://github.com/ericyoc/find_random_point_in_circle_diff_meth_poc/raw/main/circle_method_visualizations/Maximum_Method_points.jpg)

**How it works:**
1. Generate two uniform random numbers u1 and u2 in [0, 1].
2. Set radius r = max(u1, u2).
3. Generate a random angle θ in [0, 2π].
4. Convert to Cartesian coordinates: (r * cos(θ), r * sin(θ)).

**Pros:** Efficient and doesn't require rejection.
**Cons:** May be less intuitive than other methods.

### 3. Square Root Method

![Square Root Method Points](https://github.com/ericyoc/find_random_point_in_circle_diff_meth_poc/raw/main/circle_method_visualizations/Square_Root_Method_points.jpg)

**How it works:**
1. Generate a uniform random number u in [0, 1].
2. Set radius r = sqrt(u).
3. Generate a random angle θ in [0, 2π].
4. Convert to Cartesian coordinates: (r * cos(θ), r * sin(θ)).

**Pros:** Efficient and doesn't require rejection.
**Cons:** Requires slightly more computation than the maximum method.

### 4. Reflecting Sum

![Reflecting Sum Points](https://github.com/ericyoc/find_random_point_in_circle_diff_meth_poc/raw/main/circle_method_visualizations/Reflecting_Sum_points.jpg)

**How it works:**
1. Generate two uniform random numbers u1 and u2 in [0, 1].
2. Set r = u1 + u2.
3. If r > 1, reflect it by setting r = 2 - r.
4. Generate a random angle θ in [0, 2π].
5. Convert to Cartesian coordinates: (r * cos(θ), r * sin(θ)).

**Pros:** Efficient and doesn't require rejection.
**Cons:** Slightly more complex than other methods.

## Uniformity Comparison

For each method, we compare the pre- and post-uniformity distributions:

### Rejection Sampling
![Rejection Sampling Uniformity](https://github.com/ericyoc/find_random_point_in_circle_diff_meth_poc/raw/main/circle_method_visualizations/Rejection_Sampling_uniformity.jpg)

### Maximum Method
![Maximum Method Uniformity](https://github.com/ericyoc/find_random_point_in_circle_diff_meth_poc/raw/main/circle_method_visualizations/Maximum_Method_uniformity.jpg)

### Square Root Method
![Square Root Method Uniformity](https://github.com/ericyoc/find_random_point_in_circle_diff_meth_poc/raw/main/circle_method_visualizations/Square_Root_Method_uniformity.jpg)

### Reflecting Sum
![Reflecting Sum Uniformity](https://github.com/ericyoc/find_random_point_in_circle_diff_meth_poc/raw/main/circle_method_visualizations/Reflecting_Sum_uniformity.jpg)

The Reflecting Sum method also uses the Irwin-Hall distribution:

![Reflecting Sum Irwin-Hall](https://github.com/ericyoc/find_random_point_in_circle_diff_meth_poc/raw/main/circle_method_visualizations/Reflecting_Sum_irwin_hall.jpg)

## Python Code Explanation

The Python script in this repository does the following:

1. Implements each of the four methods for generating random points in a circle.
2. Generates a specified number of points (default 3141) using each method.
3. Visualizes the results for each method:
   - Distribution of points within the circle
   - Histogram of radii
   - Pre- and post-uniformity plots
   - Irwin-Hall distribution for the Reflecting Sum method
4. Saves all visualizations as .jpg files in a 'circle_method_visualizations' directory.
5. Displays the visualizations on screen.
6. Calculates and displays performance metrics (processing time and point density) for each method.
7. Provides a detailed explanation of how each method works.

The code uses libraries such as NumPy for numerical computations, Matplotlib for plotting, and PrettyTable for formatting the output table.

To run the code, ensure you have the required libraries installed and simply execute the Python script. It will generate all visualizations, save them to disk, display them on screen, and print explanations and performance metrics to the console.

This project provides a comprehensive comparison of different methods for generating random points in a circle, useful for various applications in mathematics, physics, and computer graphics.

## Disclaimer
This repository is for educational purposes only. 
