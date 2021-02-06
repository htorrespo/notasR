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
minorNOx <- c(42.41, 3.01, 19.78, 1.95, 19.78, 4.54, 8.12, 0.04, 0.24, 0.12)
par(mfrow = c(1, 2))

pie(mayorNOx, labels = mayorNOx, col = 1:2, cex = 2)
pie(minorNOx, labels = minorNOx, col = rainbow(10), cex = 2)

par(mfrow = c(1, 1))
```
However, the best pie chart color palettes may be the ones of the brewer.pal 
function of the RColorBrewer package.

```terminal
# Example 6
install.packages("RColorBrewer")
library(RColorBrewer)
```


```terminal
# Example 7
mayorNOx <- c(99.6, 0.4)
color <- brewer.pal(length(mayorNOx), "Set2") 
pie(mayorNOx, labels = paste0(mayorNOx, "%"), col = color)

minorNOx <- c(42.41, 3.01, 19.78, 1.95, 19.78, 4.54, 8.12, 0.04, 0.24, 0.12)
color <- brewer.pal(length(minorNOx), "Set2") 
pie(minorNOx, labels = paste0(minorNOx, "%"), col = color)
```
After much experimentation, I came up with the 25 colors that are mostly distinguishable. 
This is intended for classed data, not continuous/sequential data.

```terminal
c25 <- c(
  "dodgerblue2", "#E31A1C", # red
  "green4",
  "#6A3D9A", # purple
  "#FF7F00", # orange
  "black", "gold1",
  "skyblue2", "#FB9A99", # lt pink
  "palegreen2",
  "#CAB2D6", # lt purple
  "#FDBF6F", # lt orange
  "gray70", "khaki2",
  "maroon", "orchid1", "deeppink1", "blue1", "steelblue4",
  "darkturquoise", "green1", "yellow4", "yellow3",
  "darkorange4", "brown"
)
pie(rep(1, 25), col = c25)
```

Or you can alternativly select the group of 30 colors

```terminal
manualcolors <- c('black','forestgreen', 'red2', 'orange', 'cornflowerblue', 
                'magenta', 'darkolivegreen4', 'indianred1', 'tan4', 'darkblue', 
                'mediumorchid1','firebrick4',  'yellowgreen', 'lightsalmon', 'tan3',
                "tan1",'darkgray', 'wheat4', '#DDAD4B', 'chartreuse', 
                'seagreen1', 'moccasin', 'mediumvioletred', 'seagreen','cadetblue1',
                "darkolivegreen1" ,"tan2" ,   "tomato3" , "#7CE3D8","gainsboro")
pie(rep(1, 30), col = manualcolors)
```

Several examles results

```terminal
#====================================================================
# Resultados de NOX
minorNOx <- c(42.41, 3.01, 19.78, 1.95, 19.78, 4.54, 8.12#, 0.24, 0.12
)
       
pie(minorNOx, labels = paste0(minorNOx, "%"), col = manualColors)

legend("topleft", legend = c('Aircraft', 'APUs', 'Construccion Norte', 
                'Construccion Occid', 'Construccion Sur', 'FENOCO', 'GSE'#, 
                #'Troncal Caribe 557', 'Troncal Caribe 558'
                ),
       fill =  c('black','forestgreen', 'red2', 'orange', 'cornflowerblue', 
                'magenta', 'darkolivegreen4'#, 'indianred1', 'tan4'
                ))

labels <- c('Aircraft', 'APUs', 'Construccion Norte', 
                'Construccion Occid', 'Construccion Sur', 'FENOCO', 'GSE'#, 
                #'Troncal Caribe 557', 'Troncal Caribe 558'
                )
manualColors <- c('black','forestgreen', 'red2', 'orange', 'cornflowerblue', 
                'magenta', 'darkolivegreen4'#, 'indianred1', 'tan4'
                )

#------------------------------------------------------------------
minorSOx <- c(74.11, 5.79, 
            #0.68, 0.07, 0.68, 
            14.16, 2.60, 1.12
            #, 0.57
            )

pie(minorSOx, labels = paste0(minorSOx, "%"), col = manualColors)

legend("topleft", legend = c('Aircraft', 'APUs', 
                #'Construccion Norte', 'Construccion Occid', 'Construccion Sur', 
                'FENOCO', 'GSE',  'Troncal Caribe 557'
                #, 'Troncal Caribe 558'
                ),
       fill =  c('black','forestgreen', 
                #'red2', 'orange', 'cornflowerblue', 
                'magenta', 'darkolivegreen4', 'indianred1'
                #, 'tan4'
                
                ))

labels <- c('Aircraft', 'APUs', 
                #'Construccion Norte', 'Construccion Occid', 'Construccion Sur', 
                'FENOCO', 'GSE',  'Troncal Caribe 557'
                #, 'Troncal Caribe 558'
                )
manualColors <- c('black','forestgreen', 
                #'red2', 'orange', 'cornflowerblue', 
                'magenta', 'darkolivegreen4', 'indianred1'
                #, 'tan4'
                )

#====================================================================
# Resultados de PM10

mayorPM10 <- c(77, 22.8)

labels <- c('Asfalto-Chimenea', 'Asfalto-Agregados')
manualColors <- c('yellowgreen', 'lightsalmon')
pie(mayorPM10, labels = paste0(mayorPM10, "%"), col = manualColors)
legend("topleft", legend = c('Asfalto-Chimenea', 'Asfalto-Agregados'
                ),
       fill =  c('yellowgreen', 'lightsalmon'
                ))

minorPM10 <- c(3.0, 1.9, 4.2, 29.1, 
                   20.9, 29.1, 3.3, 4.8, 
                   2.0, 1.0 )

labels <- c('Aircraft', 'APUs', 'Bloqueras', 'Construccion Norte', 
            'Construccion Occid', 'Construccion Sur', 'FENOCO', 'GSE', 
            'Troncal Caribe 557', 'Troncal Caribe 558' )

manualColors <- c('forestgreen', 'red2', 'orange', 'cornflowerblue', 
                'magenta', 'darkolivegreen4', 'indianred1', 'mediumorchid1',
                'black', 'tan4' )

pie(minorPM10, labels = paste0(minorPM10, "%"), col = manualColors)
legend("topleft", legend = c('Aircraft', 'APUs', 'Bloqueras', 'Construccion Norte', 
            'Construccion Occid', 'Construccion Sur', 'FENOCO', 'GSE', 
            'Troncal Caribe 557', 'Troncal Caribe 558' 
                ),
       fill =  c('forestgreen', 'red2', 'orange', 'cornflowerblue', 
                'magenta', 'darkolivegreen4', 'indianred1', 'mediumorchid1',
                'black', 'tan4'
                ))

#------------------------------------------------------------------
# Resultados de PM2.5

mayorPM2.5 <- c(85.8, 14.1)

labels <- c('Asfalto-Chimenea', 'Asfalto-Agregados')
manualColors <- c('yellowgreen', 'lightsalmon')
pie(mayorPM2.5, labels = paste0(mayorPM2.5, "%"), col = manualColors)
legend("topleft", legend = c('Asfalto-Chimenea', 'Asfalto-Agregados'
                ),
       fill =  c('yellowgreen', 'lightsalmon'
                ))

minorPM2.5 <- c(6, 3.7, 8.3, 24.4, 
               10.1, 24.4, 6.5, 9.2, 
               4.1, 2.1)

labels <- c('Aircraft', 'APUs', 'Bloqueras', 'Construccion Norte', 
            'Construccion Occid', 'Construccion Sur', 'FENOCO', 'GSE', 
            'Troncal Caribe 557', 'Troncal Caribe 558' )

manualColors <- c('forestgreen', 'red2', 'orange', 'cornflowerblue', 
                'magenta', 'darkolivegreen4', 'indianred1', 'mediumorchid1',
                'black', 'tan4' )

pie(minorPM2.5, labels = paste0(minorPM2.5, "%"), col = manualColors)
legend("topleft", legend = c('Aircraft', 'APUs', 'Bloqueras', 'Construccion Norte', 
            'Construccion Occid', 'Construccion Sur', 'FENOCO', 'GSE', 
            'Troncal Caribe 557', 'Troncal Caribe 558' 
                ),
       fill =  c('forestgreen', 'red2', 'orange', 'cornflowerblue', 
                'magenta', 'darkolivegreen4', 'indianred1', 'mediumorchid1',
                'black', 'tan4'
                ))

#====================================================================
# Escenario 2050

# Resultados de NOX
NOx2050 <- c(87.8, 5.5, 2.3, 3.1)

labels <- c('Aircraft', 'APUs', 'FENOCO', 'GSE' )
manualColors <- c('mediumvioletred','forestgreen', 'red2', 'orange' )

pie(NOx2050, labels = paste0(NOx2050, "%"), col = manualColors)

legend("topleft", legend = c('Aircraft', 'APUs', 'FENOCO', 'GSE' ),
       fill =  c('mediumvioletred','forestgreen', 'red2', 'orange' ))

#------------------------------------------------------------------
# Resultados de SOX
SOx2050 <- c(83.5, 6.2, 4.2, 2.7, 2 )

labels <- c('Aircraft', 'APUs', 'FENOCO', 'GSE' )
manualColors <- c('darkolivegreen1','forestgreen', 'red2', 'orange', 'magenta' )
pie(SOx2050, labels = paste0(SOx2050, "%"), col = manualColors)

legend("topleft", legend = c('Aircraft', 'APUs', 'FENOCO', 'GSE', 'Ingreso Aeropuerto' ),
       fill =  c('darkolivegreen1','forestgreen', 'red2', 'orange', 'magenta' ))

#====================================================================
# Escenario 2050

# Resultados de particulas PM10
PM10_2050 <- c( 16.4, 11.3, 27.5, 5.5, 6.1, 21.4, 7.3, 4.1)

labels <- c('Aircraft', 'APUs', 'Bloqueras', 'FENOCO',
                   'GSE', 'Ingreso Aeropuerto', 'Troncal Caribe 557', ' Troncal Caribe 558' )
manualColors <- c('seagreen1', 'moccasin', 'mediumvioletred', 'seagreen','cadetblue1',
                'darkolivegreen1' , 'tan2' , 'tomato3' )
pie(PM10_2050, labels = paste0(PM10_2050, "%"), col = manualColors)

legend("topleft", legend = c('Aircraft', 'APUs', 'Bloqueras', 'FENOCO',
                   'GSE', 'Ingreso Aeropuerto', 'Troncal Caribe 557', 'Troncal Caribe 558' ),
       fill =  c('seagreen1', 'moccasin', 'mediumvioletred', 'seagreen','cadetblue1',
                'darkolivegreen1', 'tan2', 'tomato3' ))

#------------------------------------------------------------------
# Resultados de particulas PM2.5
PM25_2050 <- c( 16.5, 11.4, 27.6, 5.5, 5.8, 21.5, 7.4, 4.1)

labels <- c('Aircraft', 'APUs', 'Bloqueras', 'FENOCO',
                   'GSE', 'Ingreso Aeropuerto', 'Troncal Caribe 557', 'Troncal Caribe 558' )
manualColors <- c('seagreen1', 'moccasin', 'mediumvioletred', 'seagreen','cadetblue1',
                'darkolivegreen1' , 'tan2' , 'tomato3' )
pie(PM25_2050, labels = paste0(PM25_2050, "%"), col = manualColors)

legend("topleft", legend = c('Aircraft', 'APUs', 'Bloqueras', 'FENOCO',
                   'GSE', 'Ingreso Aeropuerto', 'Troncal Caribe 557', ' Troncal Caribe 558' ),
       fill =  c('seagreen1', 'moccasin', 'mediumvioletred', 'seagreen','cadetblue1',
                'darkolivegreen1', 'tan2', 'tomato3' ))

```
