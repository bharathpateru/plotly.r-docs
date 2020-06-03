---
description: How to create Radar Charts in R with Plotly.
display_as: scientific
language: r
layout: base
name: Radar Charts
order: 11
output:
  html_document:
    keep_md: true
permalink: r/radar-chart/
thumbnail: thumbnail/radar.gif
---


#### Basic Radar Charts


```r
library(plotly)

fig <- plot_ly(
    type = 'scatterpolar',
    r = c(39, 28, 8, 7, 28, 39),
    theta = c('A','B','C', 'D', 'E', 'A'),
    fill = 'toself'
  ) 
fig <- fig %>%
  layout(
    polar = list(
      radialaxis = list(
        visible = T,
        range = c(0,50)
      )
    ),
    showlegend = F
  )

fig
```

<div id="htmlwidget-2039759da4b3ffaed002" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-2039759da4b3ffaed002">{"x":{"visdat":{"6f7943cfce70":["function () ","plotlyVisDat"]},"cur_data":"6f7943cfce70","attrs":{"6f7943cfce70":{"r":[39,28,8,7,28,39],"theta":["A","B","C","D","E","A"],"fill":"toself","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"polar":{"radialaxis":{"visible":true,"range":[0,50]}},"showlegend":false,"hovermode":"closest"},"source":"A","config":{"showSendToCloud":false},"data":[{"fillcolor":"rgba(31,119,180,0.5)","r":[39,28,8,7,28,39],"theta":["A","B","C","D","E","A"],"fill":"toself","type":"scatterpolar","mode":"markers","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"line":{"color":"rgba(31,119,180,1)"},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#### Multiple Trace Radar Charts


```r
library(plotly)

fig <- plot_ly(
    type = 'scatterpolar',
    fill = 'toself'
  ) 
fig <- fig %>%
  add_trace(
    r = c(39, 28, 8, 7, 28, 39),
    theta = c('A','B','C', 'D', 'E', 'A'),
    name = 'Group A'
  ) 
fig <- fig %>%
  add_trace(
    r = c(1.5, 10, 39, 31, 15, 1.5),
    theta = c('A','B','C', 'D', 'E', 'A'),
    name = 'Group B'
  ) 
fig <- fig %>%
  layout(
    polar = list(
      radialaxis = list(
        visible = T,
        range = c(0,50)
      )
    )
  )

fig
```

<div id="htmlwidget-af2a0bb11d203f10980e" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-af2a0bb11d203f10980e">{"x":{"visdat":{"6f797e714e3d":["function () ","plotlyVisDat"]},"cur_data":"6f797e714e3d","attrs":{"6f797e714e3d":{"fill":"toself","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar"},"6f797e714e3d.1":{"fill":"toself","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":[39,28,8,7,28,39],"theta":["A","B","C","D","E","A"],"name":"Group A","inherit":true},"6f797e714e3d.2":{"fill":"toself","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatterpolar","r":[1.5,10,39,31,15,1.5],"theta":["A","B","C","D","E","A"],"name":"Group B","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"polar":{"radialaxis":{"visible":true,"range":[0,50]}},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"fillcolor":"rgba(31,119,180,0.5)","fill":"toself","type":"scatterpolar","mode":"markers","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"line":{"color":"rgba(31,119,180,1)"},"frame":null},{"fillcolor":"rgba(255,127,14,0.5)","fill":"toself","type":"scatterpolar","r":[39,28,8,7,28,39],"theta":["A","B","C","D","E","A"],"name":"Group A","mode":"markers","marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"line":{"color":"rgba(255,127,14,1)"},"frame":null},{"fillcolor":"rgba(44,160,44,0.5)","fill":"toself","type":"scatterpolar","r":[1.5,10,39,31,15,1.5],"theta":["A","B","C","D","E","A"],"name":"Group B","mode":"markers","marker":{"color":"rgba(44,160,44,1)","line":{"color":"rgba(44,160,44,1)"}},"line":{"color":"rgba(44,160,44,1)"},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#### Reference

See [https://plotly.com/r/reference/#scatterpolar](https://plotly.com/r/reference/#scatterpolar) for more information and options!
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
