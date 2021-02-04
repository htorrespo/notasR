## Pie Charts

Syntax

The basic syntax for creating a pie-chart using the R is −

pie(x, labels, radius, main, col, clockwise)

Following is the description of the parameters used −

- __x__ is a vector containing the numeric values used in the pie chart.
- __labels__ is used to give description to the slices.
- __radius__ indicates the radius of the circle of the pie chart.(value between −1 and +1).
- __main__ indicates the title of the chart.
- __col__ indicates the color palette.
- __clockwise__ is a logical value indicating if the slices are drawn clockwise or anti clockwise.

A very simple pie-chart is created using just the input vector and labels. The below 
script will create and save the pie chart in the current R working directory.

```terminal
# Example 1
# Create data for the graph.
x <- c(21, 62, 10, 53)
labels <- c("London", "New York", "Singapore", "Mumbai")

# Give the chart file a name.
png(file = "city.png")

# Plot the chart.
pie(x,labels)

# Save the file.
dev.off()
```
```terminal
# Example 2
# Create data for the graph.
x <- c(21, 62, 10, 53)
labels <- c("London", "New York", "Singapore", "Mumbai")

# Give the chart file a name.
png(file = "city_title_colours.jpg")

# Plot the chart with title and rainbow color pallet.
pie(x, labels, main = "City pie chart", col = rainbow(length(x)))

# Save the file.
dev.off()
```
