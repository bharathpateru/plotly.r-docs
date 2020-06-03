---
description: How to create plots using WebGL
display_as: basic
language: r
layout: base
name: WebGL vs SVG in R
order: 6
output:
  html_document:
    highlight: null
    keep_md: true
    theme: null
permalink: r/webgl-vs-svg/
redirect_from: r/webgl-vs-svg-line-chart/
thumbnail: thumbnail/webgl.jpg
---


# WebGL vs SVG in R

Recent versions of the R package include the `toWebGL()` function, which converts any eligible SVG graph into a WebGL plot. With WebGL, we can render way more elements in the browser.

## WebGL with 50,000 points


```r
library(plotly)
p <- ggplot(data = diamonds, aes(x = carat, y = price, color = cut)) +
  geom_point(alpha = 0.01)
fig <- ggplotly(p)
fig <- fig %>% toWebGL()

fig
```

<div id="htmlwidget-144b453d2a4fdc992393" style="width:672px;height:480px;" class="plotly html-widget"></div>

## More examples

* [Compare SVG performance to WebGL](https://plotly.com/r/webgl-vs-svg/)
* [WebGL with 1 million points](https://plotly.com/r/webgl-vs-svg-million-points/)
* [WebGL for time series](https://plotly.com/r/webgl-vs-svg-time-series/)
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