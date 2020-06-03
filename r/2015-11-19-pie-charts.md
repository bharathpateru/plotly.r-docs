---
description: How to make pie charts in R using plotly.
display_as: basic
language: r
layout: base
name: Pie Charts
order: 4
output:
  html_document:
    keep_md: true
page_type: example_index
permalink: r/pie-charts/
thumbnail: thumbnail/pie-chart.jpg
---


### Basic Pie Chart


```r
library(plotly)

USPersonalExpenditure <- data.frame("Categorie"=rownames(USPersonalExpenditure), USPersonalExpenditure)
data <- USPersonalExpenditure[,c('Categorie', 'X1960')]

fig <- plot_ly(data, labels = ~Categorie, values = ~X1960, type = 'pie')
fig <- fig %>% layout(title = 'United States Personal Expenditures by Categories in 1960',
         xaxis = list(showgrid = FALSE, zeroline = FALSE, showticklabels = FALSE),
         yaxis = list(showgrid = FALSE, zeroline = FALSE, showticklabels = FALSE))

fig
```

<div id="htmlwidget-98d85489566780ea343a" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-98d85489566780ea343a">{"x":{"visdat":{"630362053124":["function () ","plotlyVisDat"]},"cur_data":"630362053124","attrs":{"630362053124":{"labels":{},"values":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"pie"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"United States Personal Expenditures by Categories in 1960","xaxis":{"showgrid":false,"zeroline":false,"showticklabels":false},"yaxis":{"showgrid":false,"zeroline":false,"showticklabels":false},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"labels":["Food and Tobacco","Household Operation","Medical and Health","Personal Care","Private Education"],"values":[86.8,46.2,21.1,5.4,3.64],"type":"pie","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(255,255,255,1)"}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Styled Pie Chart


```r
library(plotly)

USPersonalExpenditure <- data.frame("Categorie" = rownames(USPersonalExpenditure), USPersonalExpenditure)
data <- USPersonalExpenditure[, c('Categorie', 'X1960')]

colors <- c('rgb(211,94,96)', 'rgb(128,133,133)', 'rgb(144,103,167)', 'rgb(171,104,87)', 'rgb(114,147,203)')

fig <- plot_ly(data, labels = ~Categorie, values = ~X1960, type = 'pie',
        textposition = 'inside',
        textinfo = 'label+percent',
        insidetextfont = list(color = '#FFFFFF'),
        hoverinfo = 'text',
        text = ~paste('$', X1960, ' billions'),
        marker = list(colors = colors,
                      line = list(color = '#FFFFFF', width = 1)),
                      #The 'pull' attribute can also be used to create space between the sectors
        showlegend = FALSE)
fig <- fig %>% layout(title = 'United States Personal Expenditures by Categories in 1960',
         xaxis = list(showgrid = FALSE, zeroline = FALSE, showticklabels = FALSE),
         yaxis = list(showgrid = FALSE, zeroline = FALSE, showticklabels = FALSE))

fig
```

<div id="htmlwidget-dff46a24eec88a847794" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-dff46a24eec88a847794">{"x":{"visdat":{"63033d8c07b1":["function () ","plotlyVisDat"]},"cur_data":"63033d8c07b1","attrs":{"63033d8c07b1":{"labels":{},"values":{},"textposition":"inside","textinfo":"label+percent","insidetextfont":{"color":"#FFFFFF"},"hoverinfo":"text","text":{},"marker":{"colors":["rgb(211,94,96)","rgb(128,133,133)","rgb(144,103,167)","rgb(171,104,87)","rgb(114,147,203)"],"line":{"color":"#FFFFFF","width":1}},"showlegend":false,"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"pie"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"United States Personal Expenditures by Categories in 1960","xaxis":{"showgrid":false,"zeroline":false,"showticklabels":false},"yaxis":{"showgrid":false,"zeroline":false,"showticklabels":false},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"labels":["Food and Tobacco","Household Operation","Medical and Health","Personal Care","Private Education"],"values":[86.8,46.2,21.1,5.4,3.64],"textposition":["inside","inside","inside","inside","inside"],"textinfo":"label+percent","insidetextfont":{"color":"#FFFFFF"},"hoverinfo":["text","text","text","text","text"],"text":["$ 86.8  billions","$ 46.2  billions","$ 21.1  billions","$ 5.4  billions","$ 3.64  billions"],"marker":{"color":"rgba(31,119,180,1)","colors":["rgb(211,94,96)","rgb(128,133,133)","rgb(144,103,167)","rgb(171,104,87)","rgb(114,147,203)"],"line":{"color":"#FFFFFF","width":1}},"showlegend":false,"type":"pie","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Subplots
In order to create pie chart subplots, you need to use the [domain](https://plotly.com/javascript/reference/#pie-domain) attribute. It is important to note that the `X` array set the horizontal position whilst the `Y` array sets the vertical. For example, `x=[0,0.5], y=[0, 0.5]` would mean the bottom left position of the plot.

```r
library(plotly)
library(dplyr)

fig <- plot_ly()
fig <- fig %>% add_pie(data = count(diamonds, cut), labels = ~cut, values = ~n,
          name = "Cut", domain = list(x = c(0, 0.4), y = c(0.4, 1)))
fig <- fig %>% add_pie(data = count(diamonds, color), labels = ~color, values = ~n,
          name = "Color", domain = list(x = c(0.6, 1), y = c(0.4, 1)))
fig <- fig %>% add_pie(data = count(diamonds, clarity), labels = ~clarity, values = ~n,
          name = "Clarity", domain = list(x = c(0.25, 0.75), y = c(0, 0.6)))
fig <- fig %>% layout(title = "Pie Charts with Subplots", showlegend = F,
         xaxis = list(showgrid = FALSE, zeroline = FALSE, showticklabels = FALSE),
         yaxis = list(showgrid = FALSE, zeroline = FALSE, showticklabels = FALSE))

fig
```

<div id="htmlwidget-34da24bda1750be828b7" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-34da24bda1750be828b7">{"x":{"visdat":{"6303482765fb":["function () ","plotlyVisDat"],"6303692a9dd8":["function () ","data"],"63032ff505ca":["function () ","data"],"630367a40d80":["function () ","data"]},"cur_data":"630367a40d80","attrs":{"6303692a9dd8":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"values":{},"labels":{},"type":"pie","name":"Cut","domain":{"x":[0,0.4],"y":[0.4,1]},"inherit":true},"63032ff505ca":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"values":{},"labels":{},"type":"pie","name":"Color","domain":{"x":[0.6,1],"y":[0.4,1]},"inherit":true},"630367a40d80":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"values":{},"labels":{},"type":"pie","name":"Clarity","domain":{"x":[0.25,0.75],"y":[0,0.6]},"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Pie Charts with Subplots","showlegend":false,"xaxis":{"showgrid":false,"zeroline":false,"showticklabels":false},"yaxis":{"showgrid":false,"zeroline":false,"showticklabels":false},"hovermode":"closest"},"source":"A","config":{"showSendToCloud":false},"data":[{"values":[1610,4906,12082,13791,21551],"labels":["Fair","Good","Very Good","Premium","Ideal"],"type":"pie","name":"Cut","domain":{"x":[0,0.4],"y":[0.4,1]},"marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(255,255,255,1)"}},"frame":null},{"values":[6775,9797,9542,11292,8304,5422,2808],"labels":["D","E","F","G","H","I","J"],"type":"pie","name":"Color","domain":{"x":[0.6,1],"y":[0.4,1]},"marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,255,255,1)"}},"frame":null},{"values":[741,9194,13065,12258,8171,5066,3655,1790],"labels":["I1","SI2","SI1","VS2","VS1","VVS2","VVS1","IF"],"type":"pie","name":"Clarity","domain":{"x":[0.25,0.75],"y":[0,0.6]},"marker":{"color":"rgba(44,160,44,1)","line":{"color":"rgba(255,255,255,1)"}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Subplots Using Grid
This example uses a plotly [grid](https://plotly.com/javascript/reference/#layout-grid) attribute for the suplots. Reference the row and column destination using the [domain](https://plotly.com/javascript/reference/#pie-domain) attribute.

```r
library(plotly)
library(dplyr)

fig <- plot_ly()
fig <- fig %>% add_pie(data = count(diamonds, cut), labels = ~cut, values = ~n,
                         name = "Cut", domain = list(row = 0, column = 0))
fig <- fig %>% add_pie(data = count(diamonds, color), labels = ~color, values = ~n,
                       name = "Color", domain = list(row = 0, column = 1))
fig <- fig %>% add_pie(data = count(diamonds, clarity), labels = ~clarity, values = ~n,
                       name = "Clarity", domain = list(row = 1, column = 0))
fig <- fig %>% add_pie(data = count(diamonds, cut), labels = ~cut, values = ~n,
                       name = "Clarity", domain = list(row = 1, column = 1))
fig <- fig %>% layout(title = "Pie Charts with Subplots", showlegend = F,
                      grid=list(rows=2, columns=2),
                      xaxis = list(showgrid = FALSE, zeroline = FALSE, showticklabels = FALSE),
                      yaxis = list(showgrid = FALSE, zeroline = FALSE, showticklabels = FALSE))

fig
```

<div id="htmlwidget-9562eda24246c2f9c7a3" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-9562eda24246c2f9c7a3">{"x":{"visdat":{"6303712eaf8d":["function () ","plotlyVisDat"],"6303164420d7":["function () ","data"],"63036c278621":["function () ","data"],"6303246cf3f5":["function () ","data"],"630367f9d75c":["function () ","data"]},"cur_data":"630367f9d75c","attrs":{"6303164420d7":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"values":{},"labels":{},"type":"pie","name":"Cut","domain":{"row":0,"column":0},"inherit":true},"63036c278621":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"values":{},"labels":{},"type":"pie","name":"Color","domain":{"row":0,"column":1},"inherit":true},"6303246cf3f5":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"values":{},"labels":{},"type":"pie","name":"Clarity","domain":{"row":1,"column":0},"inherit":true},"630367f9d75c":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"values":{},"labels":{},"type":"pie","name":"Clarity","domain":{"row":1,"column":1},"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Pie Charts with Subplots","showlegend":false,"grid":{"rows":2,"columns":2},"xaxis":{"showgrid":false,"zeroline":false,"showticklabels":false},"yaxis":{"showgrid":false,"zeroline":false,"showticklabels":false},"hovermode":"closest"},"source":"A","config":{"showSendToCloud":false},"data":[{"values":[1610,4906,12082,13791,21551],"labels":["Fair","Good","Very Good","Premium","Ideal"],"type":"pie","name":"Cut","domain":{"row":0,"column":0},"marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(255,255,255,1)"}},"frame":null},{"values":[6775,9797,9542,11292,8304,5422,2808],"labels":["D","E","F","G","H","I","J"],"type":"pie","name":"Color","domain":{"row":0,"column":1},"marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,255,255,1)"}},"frame":null},{"values":[741,9194,13065,12258,8171,5066,3655,1790],"labels":["I1","SI2","SI1","VS2","VS1","VVS2","VVS1","IF"],"type":"pie","name":"Clarity","domain":{"row":1,"column":0},"marker":{"color":"rgba(44,160,44,1)","line":{"color":"rgba(255,255,255,1)"}},"frame":null},{"values":[1610,4906,12082,13791,21551],"labels":["Fair","Good","Very Good","Premium","Ideal"],"type":"pie","name":"Clarity","domain":{"row":1,"column":1},"marker":{"color":"rgba(214,39,40,1)","line":{"color":"rgba(255,255,255,1)"}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

See more examples of subplots [here](https://plotly.com/r/subplots/).

#### Controlling text orientation inside sunburst sectors

The `insidetextorientation` attribute controls the orientation of text inside sectors. With "auto" the texts may automatically be rotated to fit with the maximum size inside the slice. Using "horizontal" (resp. "radial", "tangential") forces text to be horizontal (resp. radial or tangential). Note that `plotly` may reduce the font size in order to fit the text with the requested orientation.


```r
library(plotly)

labels = c('Oxygen','Hydrogen','Carbon_Dioxide','Nitrogen')
values = c(4500, 2500, 1053, 500)

fig <- plot_ly(type='pie', labels=labels, values=values, 
               textinfo='label+percent',
               insidetextorientation='radial')
fig
```

<div id="htmlwidget-b9e7984ca333f0111621" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-b9e7984ca333f0111621">{"x":{"visdat":{"63034a90a690":["function () ","plotlyVisDat"]},"cur_data":"63034a90a690","attrs":{"63034a90a690":{"labels":["Oxygen","Hydrogen","Carbon_Dioxide","Nitrogen"],"values":[4500,2500,1053,500],"textinfo":"label+percent","insidetextorientation":"radial","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"pie"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"hovermode":"closest","showlegend":true},"source":"A","config":{"showSendToCloud":false},"data":[{"labels":["Oxygen","Hydrogen","Carbon_Dioxide","Nitrogen"],"values":[4500,2500,1053,500],"textinfo":"label+percent","insidetextorientation":"radial","type":"pie","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(255,255,255,1)"}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>
### Donut Chart


```r
library(plotly)
library(dplyr)

# Get Manufacturer
mtcars$manuf <- sapply(strsplit(rownames(mtcars), " "), "[[", 1)

df <- mtcars
df <- df %>% group_by(manuf)
df <- df %>% summarize(count = n())
fig <- df %>% plot_ly(labels = ~manuf, values = ~count)
fig <- fig %>% add_pie(hole = 0.6)
fig <- fig %>% layout(title = "Donut charts using Plotly",  showlegend = F,
                      xaxis = list(showgrid = FALSE, zeroline = FALSE, showticklabels = FALSE),
                      yaxis = list(showgrid = FALSE, zeroline = FALSE, showticklabels = FALSE))

fig
```

<div id="htmlwidget-fb5e8dba3a0b7dc553bd" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-fb5e8dba3a0b7dc553bd">{"x":{"visdat":{"6303bc86fa1":["function () ","plotlyVisDat"]},"cur_data":"6303bc86fa1","attrs":{"6303bc86fa1":{"labels":{},"values":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"pie","hole":0.6,"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Donut charts using Plotly","showlegend":false,"xaxis":{"showgrid":false,"zeroline":false,"showticklabels":false},"yaxis":{"showgrid":false,"zeroline":false,"showticklabels":false},"hovermode":"closest"},"source":"A","config":{"showSendToCloud":false},"data":[{"labels":["AMC","Cadillac","Camaro","Chrysler","Datsun","Dodge","Duster","Ferrari","Fiat","Ford","Honda","Hornet","Lincoln","Lotus","Maserati","Mazda","Merc","Pontiac","Porsche","Toyota","Valiant","Volvo"],"values":[1,1,1,1,1,1,1,1,2,1,1,2,1,1,1,2,7,1,1,2,1,1],"type":"pie","hole":0.6,"marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(255,255,255,1)"}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#Reference

See [https://plotly.com/r/reference/#pie](https://plotly.com/r/reference/#pie) for more information and chart attribute options!
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
