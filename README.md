# Massive-Data-Cleaning-&-Plotting
![Julia](https://img.shields.io/badge/Julia-1.6%2B-9558B2?style=for-the-badge&logo=julia)
![Plots.jl](https://img.shields.io/badge/Plots.jl-Enabled-blue?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

A specialized Julia utility designed to parse numerical values from raw text logs and generate structured visual comparisons. This tool is ideal for researchers or engineers who need to turn unstructured console output into readable trend charts.

## 🛠 Features
- **Regex-Based Extraction**: Robustly captures integers, floats, and scientific notation (e.g., `1.2e-5`).
- **Context-Aware Parsing**: Categorizes data based on specific "anchor" sentences.
- **Stacked Visualization**: Produces two distinct plots sharing a common X-axis for comparative analysis.
- **Automated Environment**: Self-installs `Plots` and `Printf` if they are missing.

---

## ⚙️ Customization (User Preferences)

The script is designed to be easily modified to suit different data formats or aesthetic preferences.

### 1. Modifying Search Patterns
To change which sentences the script looks for, update the strings in the `if` and `elseif` conditions:
* Change `"Sentence previous to data"` to your specific log prefix.
* The **Regex** `regex = r"gives\s+([-\d.eE+]+)"` can be adjusted if your data follows a word other than "gives".

### 2. Plot Aesthetics
You can customize the appearance of the graphs in the **PLOTTING** section:
* **Colors & Labels**: Change `label`, `title`, or `ylabel` strings to match your data type.
* **Axis Scaling**: The second plot uses `ylims=(0, 1)`. Remove this line for automatic scaling or change the values to your preferred range.
* **Dimensions**: Adjust `size = (800, 700)` in the `display` function to change the window size.

### 3. Layout Control
The script currently uses a vertical stack: `layout = (2, 1)`. 
* For side-by-side plots, change it to `layout = (1, 2)`.

---

## 🚀 How to Use

1.  **Input Data**: Paste your raw text inside the `data = """ ... """` block.
2.  **Configuration**: Ensure the `contains(line, "...")` strings match your text format.
3.  **Execution**: Run the script in your terminal:
    ```bash
    julia script_name.jl
    ```



## 📊 Data Logic & Requirements

| Component | Description |
| :--- | :--- |
| **Language** | Julia 1.x |
| **Libraries** | `Plots.jl`, `Printf.jl` |
| **X-Axis** | Automatically indexed based on the number of captured values. |
| **Y-Axis** | Data 1 (Auto-scale) / Data 2 (Fixed 0.0 - 1.0). |

---

## 📝 Troubleshooting Note
Ensure your variable names match throughout the script. If you define `Data1_values`, ensure the `push!` function targets `Data1_values` rather than a shortened name like `Data1` to avoid `UndefVarError`.
