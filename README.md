# Massive-Data-Cleaning-&-Plotting
# Log Data Parser & Visualizer in Julia

![Julia](https://img.shields.io/badge/Julia-1.6%2B-9558B2?style=for-the-badge&logo=julia)
![Plots.jl](https://img.shields.io/badge/Plots.jl-Enabled-blue?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

A lightweight Julia utility to **parse unstructured text logs**, extract numerical data using Regular Expressions, and visualize the results instantly.

## 📝 Overview

This script takes raw text input (e.g., console logs, simulation outputs), scans for specific keywords, and extracts associated numerical values. It then generates a comparative visualization of the extracted datasets.

**Primary functions:**
1.  **Parses** raw text for lines containing specific target phrases.
2.  **Extracts** floating-point numbers (including scientific notation) using Regex.
3.  **Visualizes** the trends using `Plots.jl` in a clean 2-row layout.



[Image of line chart data visualization]


## ⚙️ How It Works

The script iterates through the input text line-by-line and applies the following logic:

* **Target 1:** Looks for lines containing `"Sentence previous to data"`.
* **Target 2:** Looks for lines containing `"Sentence previous to other data"`.
* **Extraction:** Uses the regex `r"gives\s+([-\d.eE+]+)"` to capture the number immediately following the word "gives".

## 🛠️ Dependencies

The script uses standard Julia libraries. It will automatically attempt to install `Plots` if not present.

* **Plots.jl:** For generating the graphs.
* **Printf:** For formatted console output.

## 🚀 Usage

1.  **Insert Data:** Open the script and paste your raw text log into the `data` variable (inside the `"""` quotes).
2.  **Run:**
    ```bash
    julia script_name.jl
    ```
3.  **Output:**
    * **Console:** Prints the count of values found for each dataset.
    * **Window:** Opens a plot window showing "Data 1" and "Data 2" stacked vertically.

## 📊 Visualization Details

The output plot is configured as follows:
* **Layout:** 2 Rows x 1 Column.
* **Data 1 (Top):** Auto-scaled Y-axis.
* **Data 2 (Bottom):** Fixed Y-axis limits (`0` to `1`).

## 📄 License

Open source. Feel free to modify the regex patterns or target phrases to match your specific log file format.
