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

```terminal
#Example 3
# Create data for the graph.
x <-  c(21, 62, 10,53)
labels <-  c("London","New York","Singapore","Mumbai")

piepercent<- round(100*x/sum(x), 1)

# Give the chart file a name.
png(file = "city_percentage_legends.jpg")

# Plot the chart.
pie(x, labels = piepercent, main = "City pie chart",col = rainbow(length(x)))
legend("topright", c("London","New York","Singapore","Mumbai"), cex = 0.8,
   fill = rainbow(length(x)))

# Save the file.
dev.off()
```
Customization

In addition, you can modify the color of the graph with the col argument. In the 
following block of code we show you how to use different color palettes. Note 
that the cex argument allows you to modify the size of the labels.

```terminal
Example 4
count <- c(7, 25, 16, 12, 10, 30)
par(mfrow = c(1, 3))

pie(count, labels = count, col = 1:6, cex = 2)
pie(count, labels = count, col = rainbow(6), cex = 2)
pie(count, labels = count, col = topo.colors(6), cex = 2)

par(mfrow = c(1, 1))
```


```terminal
# Example 5
mayorNOx <- c(99.6, 0.4)
minorNOx <- c(54562.35, 3874.26, 25448.33, 2514.24, 25448.33, 5835.91, 10443.35, 57.73, 302.96, 155.77)
par(mfrow = c(1, 2))

pie(mayorNOx, labels = mayorNOx, col = 1:2, cex = 2)
pie(minorNOx, labels = minorNOx, col = rainbow(10), cex = 2)

par(mfrow = c(1, 1))
```
However, the best pie chart color palettes may be the ones of the brewer.pal 
function of the RColorBrewer package.

```terminal
install.packages("RColorBrewer")
library(RColorBrewer)
```


