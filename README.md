# Karatsuba-Mandelbrot Interactive Visualizer

This project provides an interactive web-based visualizer that combines the Karatsuba multiplication algorithm with a dynamic Mandelbrot set visualization. It aims to demonstrate the efficiency of the Karatsuba algorithm compared to traditional multiplication methods while simultaneously generating a unique Mandelbrot fractal influenced by the input numbers.

## Features

* **Karatsuba Algorithm Demonstration**: Input two numbers, and the visualizer will calculate their product using the Karatsuba algorithm, displaying the number of operations performed.
* **Traditional Multiplication Comparison**: Alongside the Karatsuba calculation, the approximate number of operations for traditional long multiplication is shown, highlighting the efficiency gain.
* **Dynamic Mandelbrot Fractal**: A Mandelbrot set is rendered, where its appearance (colors, scaling, rotation, and escape radius) is dynamically influenced by the input numbers and their product/sum.
* **Interactive Controls**: Adjust input numbers, maximum iterations for the fractal, and resolution of the fractal rendering on the fly.
* **Performance Statistics**: View real-time statistics on Karatsuba operations, traditional operations, efficiency gain, and the final multiplication result.
* **Algorithm Steps Explained**: A concise explanation of the Karatsuba algorithm's steps is provided directly on the page.
* **Loading Indicator**: A loading spinner and progress bar are displayed during fractal generation for better user experience.

## Technologies Used

* **HTML5**: For structuring the web page content.
* **CSS3**: For styling and layout, including responsive design and visually appealing gradients and effects.
* **JavaScript (ES6+)**: For implementing the Karatsuba algorithm, Mandelbrot fractal generation, interactive controls, and dynamic updates.
* **Canvas API**: Used for drawing the Mandelbrot fractal efficiently.

## How to Use

To run this project, simply open the `newfirst.html` file in your web browser. There are no special server requirements.

1.  **Open `newfirst.html`**: Navigate to the directory where you saved `newfirst.html` and open it with your preferred web browser (e.g., Chrome, Firefox, Edge).

2.  **Input Numbers**: In the "Controls" section at the top, enter two numbers between 100 and 99999 into the "Number 1" and "Number 2" fields.

3.  **Adjust Fractal Parameters**:
    * **Max Iterations**: Use the slider to set the maximum number of iterations for the Mandelbrot calculation. Higher values result in more detail but take longer to render.
    * **Resolution**: Use the slider to set the resolution of the fractal canvas. Higher resolutions provide sharper images but increase rendering time.

4.  **Generate Visualization**:
    * Click the "Generate" button to start the calculation and fractal rendering with the current parameters.
    * The visualization will also auto-update after a short delay when you change any input values.

5.  **Observe Results**:
    * The "Karatsuba Algorithm Visualization" panel will display the generated fractal.
    * Below the canvas, "Karatsuba Operations", "Traditional Operations", "Efficiency Gain", and "Multiplication Result" statistics will update.
    * The "Current calculation" in the "Multiplication Demo" section will show the numbers being multiplied and their result.

6.  **Reset**: Click the "Reset" button to revert all input fields to their default values (Number 1: 1234, Number 2: 5678, Max Iterations: 50, Resolution: 200) and regenerate the visualization.

## Karatsuba Algorithm Explained

The Karatsuba algorithm is a fast multiplication algorithm that reduces the multiplication of two $n$-digit numbers to at most $3n^{\log_2 3} \approx 3n^{1.585}$ single-digit multiplications, instead of the $n^2$ multiplications required by the traditional long multiplication method. This makes it asymptotically faster for large numbers.

The core idea involves a divide-and-conquer approach:

* **Step 1: Split Numbers**: Given two numbers $x$ and $y$, split them into high ($x_1, y_1$) and low ($x_0, y_0$) parts.
    $x = x_1 \times 10^m + x_0$
    $y = y_1 \times 10^m + y_0$
    where $m$ is approximately half the number of digits.

* **Step 2: Calculate Three Products**: Instead of four recursive multiplications as in standard divide-and-conquer, Karatsuba performs three:
    * $P_1 = x_1 \times y_1$
    * $P_2 = x_0 \times y_0$
    * $P_3 = (x_1 + x_0) \times (y_1 + y_0) - P_1 - P_2$ (This cleverly derives the cross-product terms $x_1 y_0 + x_0 y_1$)

* **Step 3: Combine Results**: The final product is then assembled using these three results:
    $Result = P_1 \times 10^{2m} + P_3 \times 10^m + P_2$

## Fractal Connection (Mandelbrot Set)

The visualization uses a modified Mandelbrot iteration formula. Each pixel on the canvas corresponds to a complex number $c = x + yi$. The iteration formula is $z_{new} = z^2 + c + \text{modifier}$, where a `modifier` is introduced based on the input numbers.

The colors of the fractal represent the "escape time" of each point – how many iterations it takes for the magnitude of $z$ to exceed a certain escape radius. The input numbers ($num1$ and $num2$) significantly influence:
* The scaling and rotation of the complex plane mapping.
* The `modifier` added to the Mandelbrot iteration.
* The escape radius used in the iteration.
* The HSL (Hue, Saturation, Lightness) color palette, creating vibrant and unique patterns based on the input values.

This dynamic linkage ensures that different input numbers generate distinct and visually interesting fractal patterns, illustrating the "complexity" stemming from seemingly simple mathematical operations.

## Development Notes

* The `karatsubaMultiply` function handles numbers by converting them to strings to work with digits, and includes base cases for small numbers.
* The `traditionalMultiplyCount` function provides a simplified operation count for traditional multiplication to highlight efficiency. It's a simulation, not a full implementation of long multiplication.
* Asynchronous operations (`async/await`) are used in `generateFractal` to update the progress bar and keep the UI responsive during intensive calculations.
* The `hslToRgb` utility function is used for generating the rich, dynamic color schemes of the fractal.

## License

This project is open-source 
To use the Karatsuba-Mandelbrot Interactive Visualizer, follow these steps:

Open newfirst.html: Locate the newfirst.html file and open it in your web browser (e.g., Chrome, Firefox, Edge).

Input Numbers: In the "Controls" section, enter two numbers between 100 and 99999 into the "Number 1" and "Number 2" fields.

Adjust Fractal Parameters:

Max Iterations: Use the slider to set the maximum number of iterations for the Mandelbrot calculation. Higher values result in more detail but take longer to render.

Resolution: Use the slider to set the resolution of the fractal canvas. Higher resolutions provide sharper images but increase rendering time.

Generate Visualization: Click the "Generate" button to start the calculation and fractal rendering with the current parameters. The visualization will also auto-update after a short delay when you change any input values.

Observe Results:

The "Karatsuba Algorithm Visualization" panel will display the generated fractal.

Below the canvas, "Karatsuba Operations", "Traditional Operations", "Efficiency Gain", and "Multiplication Result" statistics will update.

The "Current calculation" in the "Multiplication Demo" section will show the numbers being multiplied and their result.

Reset: Click the "Reset" button to revert all input fields to their default values (Number 1: 1234, Number 2: 5678, Max Iterations: 50, Resolution: 200) and regenerate the visualization.
