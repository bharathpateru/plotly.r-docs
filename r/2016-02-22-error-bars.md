---
description: How to add error bars to plots in R.
display_as: statistical
language: r
layout: base
name: Error Bars
order: 4
output:
  html_document:
    keep_md: true
page_type: example_index
permalink: r/error-bars/
thumbnail: thumbnail/error-bar.jpg
---


### Bar Chart with Error Bars


```r
library(plotly)
library(plyr)

data_mean <- ddply(ToothGrowth, c("supp", "dose"), summarise, length = mean(len))
data_sd <- ddply(ToothGrowth, c("supp", "dose"), summarise, length = sd(len))
data <- data.frame(data_mean, data_sd$length)
data <- rename(data, c("data_sd.length" = "sd"))
data$dose <- as.factor(data$dose)

fig <- plot_ly(data = data[which(data$supp == 'OJ'),], x = ~dose, y = ~length, type = 'bar', name = 'OJ',
        error_y = ~list(array = sd,
                        color = '#000000'))
fig <- fig %>% add_trace(data = data[which(data$supp == 'VC'),], name = 'VC')

fig
```

<div id="htmlwidget-208abdd7a5989c072bf8" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-208abdd7a5989c072bf8">{"x":{"visdat":{"63dd2c18a072":["function () ","plotlyVisDat"],"63dd5dcc896a":["function () ","data"]},"cur_data":"63dd5dcc896a","attrs":{"63dd2c18a072":{"x":{},"y":{},"error_y":{},"name":"OJ","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar"},"63dd5dcc896a":{"x":{},"y":{},"error_y":{},"name":"VC","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":"dose","type":"category","categoryorder":"array","categoryarray":["0.5","1","2"]},"yaxis":{"domain":[0,1],"automargin":true,"title":"length"},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"x":["0.5","1","2"],"y":[13.23,22.7,26.06],"error_y":{"color":"#000000","array":[4.45970851065403,3.91095327964367,2.65505806590615]},"name":"OJ","type":"bar","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_x":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":["0.5","1","2"],"y":[7.98,16.77,26.14],"error_y":{"color":"#000000","array":[2.74663430401646,2.51530868439199,4.79773094516796]},"name":"VC","type":"bar","marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"error_x":{"color":"rgba(255,127,14,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Scatterplot with Error Bars


```r
library(plotly)
library(plyr)

data_mean <- ddply(ToothGrowth, c("supp", "dose"), summarise, length = mean(len))
data_sd <- ddply(ToothGrowth, c("supp", "dose"), summarise, length = sd(len))
data <- data.frame(data_mean, data_sd$length)
data <- rename(data, c("data_sd.length" = "sd"))
data$dose <- as.factor(data$dose)

fig <- plot_ly(data = data[which(data$supp == 'OJ'),], x = ~dose, y = ~length, type = 'scatter', mode = 'markers',
        name = 'OJ',
        error_y = ~list(array = sd,
                        color = '#000000'))
fig <- fig %>% add_trace(data = data[which(data$supp == 'VC'),], name = 'VC')

fig
```

<div id="htmlwidget-3dbb44692ab67d8ee2ce" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-3dbb44692ab67d8ee2ce">{"x":{"visdat":{"63dd1ff48417":["function () ","plotlyVisDat"],"63dd36c8a1a6":["function () ","data"]},"cur_data":"63dd36c8a1a6","attrs":{"63dd1ff48417":{"x":{},"y":{},"mode":"markers","error_y":{},"name":"OJ","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"},"63dd36c8a1a6":{"x":{},"y":{},"mode":"markers","error_y":{},"name":"VC","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":"dose","type":"category","categoryorder":"array","categoryarray":["0.5","1","2"]},"yaxis":{"domain":[0,1],"automargin":true,"title":"length"},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"x":["0.5","1","2"],"y":[13.23,22.7,26.06],"mode":"markers","error_y":{"color":"#000000","array":[4.45970851065403,3.91095327964367,2.65505806590615]},"name":"OJ","type":"scatter","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":["0.5","1","2"],"y":[7.98,16.77,26.14],"mode":"markers","error_y":{"color":"#000000","array":[2.74663430401646,2.51530868439199,4.79773094516796]},"name":"VC","type":"scatter","marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"error_x":{"color":"rgba(255,127,14,1)"},"line":{"color":"rgba(255,127,14,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Line Graph with Error Bars


```r
library(plotly)
library(plyr)

data_mean <- ddply(ToothGrowth, c("supp", "dose"), summarise, length = mean(len))
data_sd <- ddply(ToothGrowth, c("supp", "dose"), summarise, length = sd(len))
data <- data.frame(data_mean, data_sd$length)
data <- rename(data, c("data_sd.length" = "sd"))
data$dose <- as.factor(data$dose)

fig <- plot_ly(data = data[which(data$supp == 'OJ'),], x = ~dose, y = ~length, type = 'scatter', mode = 'lines+markers',
        name = 'OJ',
        error_y = ~list(array = sd,
                        color = '#000000'))
fig <- fig %>% add_trace(data = data[which(data$supp == 'VC'),], name = 'VC')

fig
```

<div id="htmlwidget-490e35f6d6be0b46834e" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-490e35f6d6be0b46834e">{"x":{"visdat":{"63dd3ee07afc":["function () ","plotlyVisDat"],"63dd2df5285a":["function () ","data"]},"cur_data":"63dd2df5285a","attrs":{"63dd3ee07afc":{"x":{},"y":{},"mode":"lines+markers","error_y":{},"name":"OJ","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"},"63dd2df5285a":{"x":{},"y":{},"mode":"lines+markers","error_y":{},"name":"VC","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":"dose","type":"category","categoryorder":"array","categoryarray":["0.5","1","2"]},"yaxis":{"domain":[0,1],"automargin":true,"title":"length"},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"x":["0.5","1","2"],"y":[13.23,22.7,26.06],"mode":"lines+markers","error_y":{"color":"#000000","array":[4.45970851065403,3.91095327964367,2.65505806590615]},"name":"OJ","type":"scatter","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":["0.5","1","2"],"y":[7.98,16.77,26.14],"mode":"lines+markers","error_y":{"color":"#000000","array":[2.74663430401646,2.51530868439199,4.79773094516796]},"name":"VC","type":"scatter","marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"error_x":{"color":"rgba(255,127,14,1)"},"line":{"color":"rgba(255,127,14,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Reference

See [https://plotly.com/r/reference](https://plotly.com/r/reference) for more information and chart attribute options!
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
