---
description: How to design figures with multiple chart types in R. An example of a
  line chart with a line of best fit and an uncertainty band.
display_as: basic
language: r
layout: base
name: Graphing Multiple Chart Types
order: 10
output:
  html_document:
    keep_md: true
permalink: r/graphing-multiple-chart-types/
thumbnail: thumbnail/mixed.jpg
---


### Bar and Line Chart


```r
library(plotly)

airquality_sept <- airquality[which(airquality$Month == 9),]
airquality_sept$Date <- as.Date(paste(airquality_sept$Month, airquality_sept$Day, 1973, sep = "."), format = "%m.%d.%Y")

fig <- plot_ly(airquality_sept)
fig <- fig %>% add_trace(x = ~Date, y = ~Wind, type = 'bar', name = 'Wind',
            marker = list(color = '#C9EFF9'),
            hoverinfo = "text",
            text = ~paste(Wind, ' mph'))
fig <- fig %>% add_trace(x = ~Date, y = ~Temp, type = 'scatter', mode = 'lines', name = 'Temperature', yaxis = 'y2',
            line = list(color = '#45171D'),
            hoverinfo = "text",
            text = ~paste(Temp, '°F'))
fig <- fig %>% layout(title = 'New York Wind and Temperature Measurements for September 1973',
         xaxis = list(title = ""),
         yaxis = list(side = 'left', title = 'Wind in mph', showgrid = FALSE, zeroline = FALSE),
         yaxis2 = list(side = 'right', overlaying = "y", title = 'Temperature in degrees F', showgrid = FALSE, zeroline = FALSE))

fig
```

<div id="htmlwidget-3f2c85c3cc0eb7747c24" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-3f2c85c3cc0eb7747c24">{"x":{"visdat":{"5d9168b8d22e":["function () ","plotlyVisDat"]},"cur_data":"5d9168b8d22e","attrs":{"5d9168b8d22e":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":{},"y":{},"type":"bar","name":"Wind","marker":{"color":"#C9EFF9"},"hoverinfo":"text","text":{},"inherit":true},"5d9168b8d22e.1":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":{},"y":{},"type":"scatter","mode":"lines","name":"Temperature","yaxis":"y2","line":{"color":"#45171D"},"hoverinfo":"text","text":{},"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"New York Wind and Temperature Measurements for September 1973","xaxis":{"domain":[0,1],"automargin":true,"title":""},"yaxis":{"domain":[0,1],"automargin":true,"side":"left","title":"Wind in mph","showgrid":false,"zeroline":false},"yaxis2":{"side":"right","overlaying":"y","title":"Temperature in degrees F","showgrid":false,"zeroline":false},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"x":["1973-09-01","1973-09-02","1973-09-03","1973-09-04","1973-09-05","1973-09-06","1973-09-07","1973-09-08","1973-09-09","1973-09-10","1973-09-11","1973-09-12","1973-09-13","1973-09-14","1973-09-15","1973-09-16","1973-09-17","1973-09-18","1973-09-19","1973-09-20","1973-09-21","1973-09-22","1973-09-23","1973-09-24","1973-09-25","1973-09-26","1973-09-27","1973-09-28","1973-09-29","1973-09-30"],"y":[6.9,5.1,2.8,4.6,7.4,15.5,10.9,10.3,10.9,9.7,14.9,15.5,6.3,10.9,11.5,6.9,13.8,10.3,10.3,8,12.6,9.2,10.3,10.3,16.6,6.9,13.2,14.3,8,11.5],"type":"bar","name":"Wind","marker":{"color":"#C9EFF9","line":{"color":"rgba(31,119,180,1)"}},"hoverinfo":["text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text"],"text":["6.9  mph","5.1  mph","2.8  mph","4.6  mph","7.4  mph","15.5  mph","10.9  mph","10.3  mph","10.9  mph","9.7  mph","14.9  mph","15.5  mph","6.3  mph","10.9  mph","11.5  mph","6.9  mph","13.8  mph","10.3  mph","10.3  mph","8  mph","12.6  mph","9.2  mph","10.3  mph","10.3  mph","16.6  mph","6.9  mph","13.2  mph","14.3  mph","8  mph","11.5  mph"],"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":["1973-09-01","1973-09-02","1973-09-03","1973-09-04","1973-09-05","1973-09-06","1973-09-07","1973-09-08","1973-09-09","1973-09-10","1973-09-11","1973-09-12","1973-09-13","1973-09-14","1973-09-15","1973-09-16","1973-09-17","1973-09-18","1973-09-19","1973-09-20","1973-09-21","1973-09-22","1973-09-23","1973-09-24","1973-09-25","1973-09-26","1973-09-27","1973-09-28","1973-09-29","1973-09-30"],"y":[91,92,93,93,87,84,80,78,75,73,81,76,77,71,71,78,67,76,68,82,64,71,81,69,63,70,77,75,76,68],"type":"scatter","mode":"lines","name":"Temperature","yaxis":"y2","line":{"color":"#45171D"},"hoverinfo":["text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text"],"text":["91 °F","92 °F","93 °F","93 °F","87 °F","84 °F","80 °F","78 °F","75 °F","73 °F","81 °F","76 °F","77 °F","71 °F","71 °F","78 °F","67 °F","76 °F","68 °F","82 °F","64 °F","71 °F","81 °F","69 °F","63 °F","70 °F","77 °F","75 °F","76 °F","68 °F"],"marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"error_y":{"color":"rgba(255,127,14,1)"},"error_x":{"color":"rgba(255,127,14,1)"},"xaxis":"x","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Scatterplot with Loess Smoother


```r
library(plotly)

fig <- plot_ly(mtcars, x = ~disp, color = I("black"))
fig <- fig %>% add_markers(y = ~mpg, text = rownames(mtcars), showlegend = FALSE)
fig <- fig %>% add_lines(y = ~fitted(loess(mpg ~ disp)),
            line = list(color = '#07A4B5'),
            name = "Loess Smoother", showlegend = TRUE)
fig <- fig %>% layout(xaxis = list(title = 'Displacement (cu.in.)'),
         yaxis = list(title = 'Miles/(US) gallon'),
         legend = list(x = 0.80, y = 0.90))

fig
```

<div id="htmlwidget-059b9143f023c0c65078" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-059b9143f023c0c65078">{"x":{"visdat":{"5d9172396877":["function () ","plotlyVisDat"]},"cur_data":"5d9172396877","attrs":{"5d9172396877":{"x":{},"color":["black"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"y":{},"type":"scatter","mode":"markers","text":["Mazda RX4","Mazda RX4 Wag","Datsun 710","Hornet 4 Drive","Hornet Sportabout","Valiant","Duster 360","Merc 240D","Merc 230","Merc 280","Merc 280C","Merc 450SE","Merc 450SL","Merc 450SLC","Cadillac Fleetwood","Lincoln Continental","Chrysler Imperial","Fiat 128","Honda Civic","Toyota Corolla","Toyota Corona","Dodge Challenger","AMC Javelin","Camaro Z28","Pontiac Firebird","Fiat X1-9","Porsche 914-2","Lotus Europa","Ford Pantera L","Ferrari Dino","Maserati Bora","Volvo 142E"],"showlegend":false,"inherit":true},"5d9172396877.1":{"x":{},"color":["black"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"y":{},"type":"scatter","mode":"lines","line":{"color":"#07A4B5"},"name":"Loess Smoother","showlegend":true,"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":"Displacement (cu.in.)"},"yaxis":{"domain":[0,1],"automargin":true,"title":"Miles/(US) gallon"},"legend":{"x":0.8,"y":0.9},"hovermode":"closest","showlegend":false},"source":"A","config":{"showSendToCloud":false},"data":[{"x":[160,160,108,258,360,225,360,146.7,140.8,167.6,167.6,275.8,275.8,275.8,472,460,440,78.7,75.7,71.1,120.1,318,304,350,400,79,120.3,95.1,351,145,301,121],"y":[21,21,22.8,21.4,18.7,18.1,14.3,24.4,22.8,19.2,17.8,16.4,17.3,15.2,10.4,10.4,14.7,32.4,30.4,33.9,21.5,15.5,15.2,13.3,19.2,27.3,26,30.4,15.8,19.7,15,21.4],"type":"scatter","mode":"markers","text":["Mazda RX4","Mazda RX4 Wag","Datsun 710","Hornet 4 Drive","Hornet Sportabout","Valiant","Duster 360","Merc 240D","Merc 230","Merc 280","Merc 280C","Merc 450SE","Merc 450SL","Merc 450SLC","Cadillac Fleetwood","Lincoln Continental","Chrysler Imperial","Fiat 128","Honda Civic","Toyota Corolla","Toyota Corona","Dodge Challenger","AMC Javelin","Camaro Z28","Pontiac Firebird","Fiat X1-9","Porsche 914-2","Lotus Europa","Ford Pantera L","Ferrari Dino","Maserati Bora","Volvo 142E"],"showlegend":false,"marker":{"color":"rgba(0,0,0,1)","line":{"color":"rgba(0,0,0,1)"}},"textfont":{"color":"rgba(0,0,0,1)"},"error_y":{"color":"rgba(0,0,0,1)"},"error_x":{"color":"rgba(0,0,0,1)"},"line":{"color":"rgba(0,0,0,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[71.1,75.7,78.7,79,95.1,108,120.1,120.3,121,140.8,145,146.7,160,160,167.6,167.6,225,258,275.8,275.8,275.8,301,304,318,350,351,360,360,400,440,460,472],"y":[31.8587265478689,30.997160511089,30.4515688818864,30.3978766914933,27.6878765636072,25.7536029023605,24.1266208899877,24.1012302593287,24.0128145822842,21.7855370304885,21.3720222888,21.2095787437194,20.1233661948189,20.1233661948189,19.5876473362003,19.5876473362003,17.8667031510564,17.3361001159279,16.6706159588599,16.6706159588599,16.6706159588599,16.3557242808806,16.3295803630335,16.1508424685288,15.6175774563292,15.5983332500748,15.4036322355415,15.4036322355415,14.3441620745589,13.0380914865063,12.2654317142106,11.7573008148926],"type":"scatter","mode":"lines","line":{"color":"#07A4B5"},"name":"Loess Smoother","showlegend":true,"marker":{"color":"rgba(0,0,0,1)","line":{"color":"rgba(0,0,0,1)"}},"textfont":{"color":"rgba(0,0,0,1)"},"error_y":{"color":"rgba(0,0,0,1)"},"error_x":{"color":"rgba(0,0,0,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Loess Smoother with Uncertainty Bounds


```r
library(plotly)
library(broom)

m <- loess(mpg ~ disp, data = mtcars)

fig <- plot_ly(mtcars, x = ~disp, color = I("black"))
fig <- fig %>% add_markers(y = ~mpg, text = rownames(mtcars), showlegend = FALSE)
fig <- fig %>% add_lines(y = ~fitted(loess(mpg ~ disp)),
            line = list(color = 'rgba(7, 164, 181, 1)'),
            name = "Loess Smoother")
fig <- fig %>% add_ribbons(data = augment(m),
              ymin = ~.fitted - 1.96 * .se.fit,
              ymax = ~.fitted + 1.96 * .se.fit,
              line = list(color = 'rgba(7, 164, 181, 0.05)'),
              fillcolor = 'rgba(7, 164, 181, 0.2)',
              name = "Standard Error")
fig <- fig %>% layout(xaxis = list(title = 'Displacement (cu.in.)'),
         yaxis = list(title = 'Miles/(US) gallon'),
         legend = list(x = 0.80, y = 0.90))

fig
```

<div id="htmlwidget-9cdb910ef801b5ff8827" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-9cdb910ef801b5ff8827">{"x":{"visdat":{"5d9154d1fd1":["function () ","plotlyVisDat"],"5d91116ae25e":["function () ","data"]},"cur_data":"5d91116ae25e","attrs":{"5d9154d1fd1":{"x":{},"color":["black"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"y":{},"type":"scatter","mode":"markers","text":["Mazda RX4","Mazda RX4 Wag","Datsun 710","Hornet 4 Drive","Hornet Sportabout","Valiant","Duster 360","Merc 240D","Merc 230","Merc 280","Merc 280C","Merc 450SE","Merc 450SL","Merc 450SLC","Cadillac Fleetwood","Lincoln Continental","Chrysler Imperial","Fiat 128","Honda Civic","Toyota Corolla","Toyota Corona","Dodge Challenger","AMC Javelin","Camaro Z28","Pontiac Firebird","Fiat X1-9","Porsche 914-2","Lotus Europa","Ford Pantera L","Ferrari Dino","Maserati Bora","Volvo 142E"],"showlegend":false,"inherit":true},"5d9154d1fd1.1":{"x":{},"color":["black"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"y":{},"type":"scatter","mode":"lines","line":{"color":"rgba(7, 164, 181, 1)"},"name":"Loess Smoother","inherit":true},"5d91116ae25e":{"x":{},"color":["black"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"ymin":{},"ymax":{},"type":"scatter","mode":"lines","hoveron":"points","fill":"toself","line":{"color":"rgba(7, 164, 181, 0.05)"},"fillcolor":"rgba(7, 164, 181, 0.2)","name":"Standard Error","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":"Displacement (cu.in.)"},"yaxis":{"domain":[0,1],"automargin":true,"title":"Miles/(US) gallon"},"legend":{"x":0.8,"y":0.9},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"x":[160,160,108,258,360,225,360,146.7,140.8,167.6,167.6,275.8,275.8,275.8,472,460,440,78.7,75.7,71.1,120.1,318,304,350,400,79,120.3,95.1,351,145,301,121],"y":[21,21,22.8,21.4,18.7,18.1,14.3,24.4,22.8,19.2,17.8,16.4,17.3,15.2,10.4,10.4,14.7,32.4,30.4,33.9,21.5,15.5,15.2,13.3,19.2,27.3,26,30.4,15.8,19.7,15,21.4],"type":"scatter","mode":"markers","text":["Mazda RX4","Mazda RX4 Wag","Datsun 710","Hornet 4 Drive","Hornet Sportabout","Valiant","Duster 360","Merc 240D","Merc 230","Merc 280","Merc 280C","Merc 450SE","Merc 450SL","Merc 450SLC","Cadillac Fleetwood","Lincoln Continental","Chrysler Imperial","Fiat 128","Honda Civic","Toyota Corolla","Toyota Corona","Dodge Challenger","AMC Javelin","Camaro Z28","Pontiac Firebird","Fiat X1-9","Porsche 914-2","Lotus Europa","Ford Pantera L","Ferrari Dino","Maserati Bora","Volvo 142E"],"showlegend":false,"marker":{"color":"rgba(0,0,0,1)","line":{"color":"rgba(0,0,0,1)"}},"textfont":{"color":"rgba(0,0,0,1)"},"error_y":{"color":"rgba(0,0,0,1)"},"error_x":{"color":"rgba(0,0,0,1)"},"line":{"color":"rgba(0,0,0,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[71.1,75.7,78.7,79,95.1,108,120.1,120.3,121,140.8,145,146.7,160,160,167.6,167.6,225,258,275.8,275.8,275.8,301,304,318,350,351,360,360,400,440,460,472],"y":[31.8587265478689,30.997160511089,30.4515688818864,30.3978766914933,27.6878765636072,25.7536029023605,24.1266208899877,24.1012302593287,24.0128145822842,21.7855370304885,21.3720222888,21.2095787437194,20.1233661948189,20.1233661948189,19.5876473362003,19.5876473362003,17.8667031510564,17.3361001159279,16.6706159588599,16.6706159588599,16.6706159588599,16.3557242808806,16.3295803630335,16.1508424685288,15.6175774563292,15.5983332500748,15.4036322355415,15.4036322355415,14.3441620745589,13.0380914865063,12.2654317142106,11.7573008148926],"type":"scatter","mode":"lines","line":{"color":"rgba(7, 164, 181, 1)"},"name":"Loess Smoother","marker":{"color":"rgba(0,0,0,1)","line":{"color":"rgba(0,0,0,1)"}},"textfont":{"color":"rgba(0,0,0,1)"},"error_y":{"color":"rgba(0,0,0,1)"},"error_x":{"color":"rgba(0,0,0,1)"},"xaxis":"x","yaxis":"y","frame":null},{"fillcolor":"rgba(7, 164, 181, 0.2)","x":[71.1,75.7,78.7,79,95.1,108,120.1,120.3,121,140.8,145,146.7,160,160,167.6,167.6,225,258,275.8,275.8,275.8,301,304,318,350,351,360,360,400,440,460,472,472,472,460,440,400,360,360,351,350,318,304,301,275.8,275.8,275.8,258,225,167.6,167.6,160,160,146.7,145,140.8,121,120.3,120.1,108,95.1,79,78.7,75.7,71.1],"type":"scatter","mode":"lines","hoveron":"points","fill":"toself","line":{"color":"rgba(7, 164, 181, 0.05)"},"name":"Standard Error","y":[29.6196922296082,28.9642153590505,28.54236726388,28.5005513255002,26.2918632250039,24.5450406587188,22.9330086278789,22.9068700881959,22.8156526764351,20.4388075375714,19.9863730553065,19.8082571439821,18.6121240511817,18.6121240511817,18.0237725351383,18.0237725351383,16.256272295313,15.5190313686595,15.0041837863646,15.0041837863646,15.0041837863646,14.9281309152598,14.9162210256684,14.7558651253728,14.2276931088279,14.2081927321474,14.0140809626356,14.0140809626356,12.8807957894151,11.0440265490691,9.74938413735661,8.84230571970769,8.84230571970769,14.6722959100775,14.7814792910646,15.0321564239434,15.8075283597026,16.7931835084474,16.7931835084474,16.9884737680022,17.0074618038304,17.5458198116849,17.7429397003985,17.7833176465014,18.3370481313552,18.3370481313552,18.3370481313552,19.1531688631963,19.4771340067998,21.1515221372622,21.1515221372622,21.6346083384561,21.6346083384561,22.6109003434567,22.7576715222934,23.1322665234057,25.2099764881334,25.2955904304616,25.3202331520966,26.9621651460022,29.0838899022106,32.2952020574863,32.3607704998928,33.0301056631275,34.0977608661297],"marker":{"color":"rgba(0,0,0,1)","line":{"color":"rgba(0,0,0,1)"}},"textfont":{"color":"rgba(0,0,0,1)"},"error_y":{"color":"rgba(0,0,0,1)"},"error_x":{"color":"rgba(0,0,0,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>



#Reference

See [https://plotly.com/r/reference/](https://plotly.com/r/reference/) for more information and chart attribute options!
### What About Dash?

[Dash for R](https://dashr.plot.ly/) is an open-source framework for building analytical applications, with no Javascript required, and it is tightly integrated with the Plotly graphing library. 

Learn about how to install Dash for R at https://dashr.plot.ly/installation.

Everywhere in this page that you see `fig`, you can display the same figure in a Dash for R application by passing it to the `figure` argument of the [`Graph` component](https://dashr.plot.ly/dash-core-components/graph) from the built-in `dashCoreComponents` package like this:


```r
library(plotly)

fig <- plot_ly() 
# fig <- fig %>% add_trace( ... )
# fig <- fig %>% layout( ... ) 

library(dash)
library(dashCoreComponents)
library(dashHtmlComponents)

app <- Dash$new()
app$layout(
    htmlDiv(
        list(
            dccGraph(figure=fig) 
        )
     )
)

app$run_server(debug=TRUE, dev_tools_hot_reload=FALSE)
```
