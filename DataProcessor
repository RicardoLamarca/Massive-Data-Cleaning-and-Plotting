using Pkg
Pkg.add("Plots")
Pkg.add("Printf")

using Plots
using Printf

# Raw text data provided by the user
data = """

"""
Data2_values = Float64[]
Data1_values = Float64[]

# A regular expression to find the number following "gives"
# This handles positive/negative numbers and scientific notation.
regex = r"gives\s+([-\d.eE+]+)"

# Split the data into lines and iterate through each one.
for line in split(data, '\n')
    if contains(line, "Sentence previous to data")
        # Try to match the regex in the line
        m = match(regex, line)
        if m !== nothing
            # If a match is found, parse the captured number and add to the list
            push!(Data1, parse(Float64, m.captures[1]))
        end
    elseif contains(line, "Sentence previous to other data")
        if m !== nothing
            push!(Data2, parse(Float64, m.captures[1]))
        end
    end
end

# 4. PLOTTING
# ---------------------------------------------------------------------------
# Create the plot for Data1 values
plot_Data1 = plot(
    1:length(Data1_values), Data1_values,
    label="Data 1",
    xlabel="x label data",
    ylabel="Data 1",
    title="Data 1 title",
    legend=:topright,
    linewidth=2
)

# Create the plot for J values
plot_Data2 = plot(
    1:length(Data2), Data2,
    label="Data 2",
    xlabel="x label data",
    ylabel="Data 2",
    title="Data 2 title",
    legend=:topright,
    linewidth=2,
    ylims=(0, 1)  # This line sets the y-axis limits from 0 to 1
)

# 5. DISPLAY
# ---------------------------------------------------------------------------
# Display both plots in a layout with two rows.
# You can also display them individually by calling `display(plot_Data1)`
# and then `display(plot_Data2)`.
display(plot(plot_Data1, plot_Data2, layout = (2, 1), size = (800, 700)))

println("Generated $(length(Data1)) Data 1 values and $(length(Data2)) Data 2 values.")
println("Displaying plots...")
